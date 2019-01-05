
# Feasibility study of implementing secp256k1 on Secure Scuttlebutt (SSB)

## Introduction

Secure-Scuttlebutt has been built with future compatibility for different crypto-primitives. This includes elliptic curve types for signing and encryption as well as hash functions used for content addressing.  Keys and hashes are represented as strings containing the key encoded to base64 followed by a delimiter, `'.'`, followed by suffix which describes the primitive used, for example `'ed25519'` or `'sha256'`.  This makes introducing new kinds of addresses much easier, but there are still a number of issues to address.

Being able to use secp256k1 keys on Scuttlebutt would mean that Scuttlebutt identities could have a corresponding Ethereum address.  This would create a bridge between the Scuttlebutt ecosystem and the Ethereum ecosystem, and allow developers to build applications which utilise both networks. 

## Aspects of Scuttlebutt which are effected

Scuttlebutt uses libsodium to derive Curve25519 keys, used for Diffie-Hellman style encryption, from Ed25519 keys, used for signing and verification. Ed25519 public keys are used to refer to peers on the network. 

To implement Secp256k1 keys, we would need to consider how do DH-style scalar multiplication in order to build shared secrets, both for use in the secret handshake and for creating encrypted messages using 'private-box'.  The implementations we have looked at give us this without converting the keys. 

## Relevant SSB modules:

### [secret handshake](https://github.com/auditdrivencrypto/secret-handshake)

This is the mechanism by which peers create a secure communication channel by means of a mutually authenticating key agreement handshake.  The handshake involves a combination of cryptographic signing, ephemeral keys, and Diffie-Hellman (DH) style shared secret derivation.

### [ssb-ref](https://github.com/ssbc/ssb-ref) 

This module provides way to validate references and addresses on SSB.  It's `isFeed` method tests if a given string is a valid feedId using a regular expression. We would need to modify this regular expression to allow for feedIds with the new suffix `.secp256k1`.

### [ssb-keys](https://github.com/ssbc/ssb-keys) 

Provides key generation, signing and verification of objects, loading keys to or from a file on disk, and encryption using `private-box`.

### [ssb-private](https://github.com/ssbc/ssb-private) 

Scuttlebot (the scuttlebutt 'server', or core process) plugin which handles private messaging by calling methods from `ssb-keys` which in turn use `private-box`.

### [private-box](https://github.com/auditdrivencrypto/private-box)

Provides encryption of private messages to multiple parties, obfuscating the identities of recipients.  Ephemeral keys, DH scalar multiplication and libsodium's 'secretbox' are used.

Secretbox provides symmetric encryption and will work regardless how we choose to generate the keys.  The scalar multiplication used to generate a shared secret can be replaced with `secp256k1-node`'s `ecdh` method (although the arguments are taken in a different order).

We have a working proof-of-concept which shows that private-box's functionality can be achieved with `secp256k1` keys.  More challenging is to get it to work with an array of recipients with a mixture of both curve25519 and secp256k1 keys.  The difficulty is that another module, 'ssb-keys' first removes the descriptive suffix (eg: `'.ed25519'`) before converting the keys and calling methods from `private-box`.  So we can't create a drop-in solution without modifying both modules. 

### [ssb-validate](https://github.com/ssbc/ssb-validate)

This module provides methods for verifying SSB messages.

Implementing a system of signing and verifying messages with users with varying types of keys is much easier than encrypting messages to multiple parties with differing key types.  This is because we only need to 'deal with' one user at time.  To create a signature, we need the message, a private key, and to know what type of private key it is.  To verify we need the message, signature, public key, and to know what type of public key it is.  Unlike DH encryption there are no difficult cases of having a combination of keys of different types.  Futhermore, Secp256k1 libraries tend to have well-developed and secure methods for signing and verification because it is the principle security mechanism used in cryptocurrencies.  

For these reasons, we feel confident that implementing signature creation and verification on SSB is possible with secp256k1 keys and have rather focused on encryption when researching this document.

## secp256k1 implementations in nodejs

[secp256k1-node](https://github.com/cryptocoinjs/secp256k1-node) based on [bitcoin core's secp256k1 C library](https://github.com/bitcoin-core/secp256k1)

[elliptic](https://github.com/indutny/elliptic) cryptography library which implements several elliptic curves, including secp256k1.  Keys are represented as BigNum ([bn.js](https://github.com/indutny/bn.js)), but these are easy to convert to Buffers to be consistent with our existing keys.

[ethereumjs/keythereum](https://github.com/ethereumjs/keythereum) gives us some functions particular to ethereum addresses, uses elliptic. 

## Deriving ethereum addresses from secp256k1 keys.

Secp256k1 public keys, in their complete form, are 64 bytes produced from concatonating the x and y values of the point on the curve.  Typically they are prefixed with an extra byte, `0x04`. 

Ethereum addresses are produced by removing the 04 prefix, taking the keccak-256 hash, and then truncating the first 12 bytes, to give us 20 bytes.  These are encoded as hex and the '0x' prefix is added.

[keythereum](https://github.com/ethereumjs/keythereum)'s `privateKeyToAddress` method makes this easy.

## Challenges

### Different length of public keys

Scuttlebutt uses Ed25519 and Curve25519 keys, where both public and secret keys have a length of 32 bytes.  Secp256k1 public keys, in their compressed form, are 33 bytes.  This is the 32 byte x-value prepended by either `0x02` or `0x03` depending on whether the y-value is odd or even.  This is a problem because some of our functions (eg: encryption using 'private-box') involve concatonating several keys to produce a shared secret.  If we have a mix of both key types, it is impossible to know when one ends and the other begins.

To overcome this, we propose that in 'private-box' messages, ed25519 public keys are prefixed with an additional byte, `0x00`.  This means that all public keys are now 33 bytes, and the first byte determines which crypto primative is used. 

### DH encryption between users with different key types

This is a difficult problem, and we are looking into different ways of producing shared secrets between keys on different curves.  It is possible to derive an 'equivalent' keypair on the other user's curve using our own secret key as the seed, and then send the corresponding public key together with the encrypted message.  But this makes it more difficult to verify who authored the message.  Since messages are also signed, this should not pose a great problem, but this is an area we would like to explore further.

Another option is to generate a new address of the alternative key type and automatically publish a public signed message containing the public key.  That is to say a user with a ed25519 address could publish a signed secp256k1 public key and vice-versa.

### Ephemeral keys must be the correct type

Both 'private-box' and 'secret-handshake' make use of ephemeral keypairs. In order to work with both types of key, we will need to generate and send one keypair for each type.  This increases complexity and message size. 

### Security

The `secp256k1-node` module explicitly states in the readme that it is an experimental library.  We would naturally want to conduct a security audit before using this module in production.

### Social aspects

This document focuses on technical challenges.  However, the SSB community is a participative ecosystem where decisions are made together. Making a significant change to the protocol will require discussion and consensus of developers and users.  If the change brings security issues or raises ideological questions it may be difficult to reach agreement.

## Conclusions

We have focussed on the technical feasibility of implementing a different elliptic curve type on SSB.  While we have identified some challenges, we feel they can be overcome, and that building a working proof-of-concept is achievable.  But we are aware that there is a long journey between having a proof-of-concept, and a real world working system that works with all the available clients with no bugs or issues. 

Furthermore, we have not explored the implications, what would be made possible and what are the potential advantages or issues.

## Related work

- [Secp256k1 experiments](https://github.com/ameba23/secp_experiments) source code of experiments we did as research for this document
- [Some SSB links to the discussion on this as well as a copy of Dominics related post](https://github.com/blockades/mmt_resources/blob/master/research/secp256k1.md)

## References

- Gavin Wood, ['Ethereum yellow paper'](http://gavwood.com/paper.pdf)
- Dominic Tarr, ['Designing a Secret Handshake, Authenticated Key Exchange as a Capability System'](http://dominictarr.github.io/secret-handshake-paper/shs.pdf)
- [Davide De Rosa, Basic blockchain programming - Elliptic Curve Keys](https://davidederosa.com/basic-blockchain-programming/elliptic-curve-keys/)
- [secp256k1 specification from the 'Standards for efficient cryptography group'](http://www.secg.org/sec2-v2.pdf)
- [A closer look at ethereum signatures - hackernoon](https://hackernoon.com/a-closer-look-at-ethereum-signatures-5784c14abecc) - quite interesting, shows how to verify signatures using solidity, among other things
- [Generating a usable Ethereum wallet and its corresponding keys](https://kobl.one/blog/create-full-ethereum-keypair-and-address/) - Command line examples using OpenSSL
- [Stackexchange - Derive a shared secret between different curves](https://crypto.stackexchange.com/questions/42127/derive-a-shared-secret-between-different-curves)
- [stackexchange - what does secp256k1 look like?](https://bitcoin.stackexchange.com/questions/21907/what-does-the-curve-used-in-bitcoin-secp256k1-look-like)
- [secp256k1 article on bitcoin wiki](https://en.bitcoin.it/wiki/Secp256k1)
