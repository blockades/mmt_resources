
# Feasibility study of implementing secp256k1 on Secure Scuttlebutt (SSB)

## Introduction

Secure-Scuttlebutt has been built with future compatibility for different crypto-primitives such as elliptic curve types and hash functions.  Keys and hashes are represented as strings containing the key encoded to base64 followed by a delimiter, `'.'`, followed by suffix which describes the primitive used, for example `'ed25519'` or `'sha256'`.  This makes introducing new kinds of addresses much easier, but there are still a number of issues to address.


## Aspects of Scuttlebutt which are effected

Scuttlebutt uses libsodium to derive Curve25519 keys, used for Diffie-Hellman style encryption, from Ed25519 keys, used for signing and verification. Ed25519 public keys are used to refer to peers on the network. 

To implement Secp256k1 keys, we would need to consider how do DH-style scalar multiplication in order to build shared secrets, both for use in the secret handshake and for creating encrypted messages using 'private-box'.  The implementations we have looked at give us this without converting the keys. 

## Relevant SSB modules:

### [secret handshake](https://github.com/auditdrivencrypto/secret-handshake)

This is the mechanism by which peers create a secure communication channel by means of a mutually authenticating key agreement handshake.  The handshake involves a combination of cryptographic signing, ephemeral keys, and Diffie-Hellman (DH) style shared secret derivation.

### [ssb-ref](https://github.com/ssbc/ssb-ref) 

This module provides way to validate references and addresses on SSB.  It's `isFeed` method tests if a given string is a valid feedId using a regular expression. We would need to modify this regular expression to allow for feedIds with the suffix '.secp256k1'.

### [ssb-keys](https://github.com/ssbc/ssb-keys) 

Provides key generation, signing and verification of objects, loading keys to or from a file on disk, and encryption using private-box.

### [ssb-private](https://github.com/ssbc/ssb-private) 

API to private box

### [private-box](https://github.com/auditdrivencrypto/private-box)

Provides encryption of private messages to multiple parties, obfuscating the identities of recipients.  Ephemeral keys, DH scalar multiplication and libsodium's 'secretbox' are used.

Secretbox provides symmetric encryption and will work regardless how we choose to generate the keys.  The scalar multiplication used to generate a shared secret can be replaced with `secp256k1`'s 

### [ssb-validate](https://github.com/ssbc/ssb-validate)

For validating SSB messages.

## secp256k1 implementations in nodejs

[secp256k1-node](https://github.com/cryptocoinjs/secp256k1-node) based on [bitcoin core's secp256k1 C library](https://github.com/bitcoin-core/secp256k1)

[elliptic](https://github.com/indutny/elliptic) cryptography library which implements several elliptic curves, including secp256k1.  Keys are represented as BigNum ([bn.js](https://github.com/indutny/bn.js)), but these are easy to convert to Buffers to be consistent with our existing keys.

[ethereumjs/keythereum](https://github.com/ethereumjs/keythereum) gives us some functions particular to ethereum addresses, uses elliptic. 

## Deriving ethereum addresses from secp256k1 keys.

Public keys, in their complete form, are 64 bytes produced from concatonating the x and y values of the point on the curve.  Typically they are preceded with an extra byte, `0x04`. 

Ethereum addresses are produced by removing the 04 prefix, taking the keccak-256 hash, and then truncating the first 12 bytes, to give us 20 bytes.  These are represent as hex and the '0x' prefix is added.


[keythereum](https://github.com/ethereumjs/keythereum)'s `privateKeyToAddress` method makes this easy.  

## Challenges

Scuttlebutt uses Ed25519 and Curve25519 keys, where both public and secret keys have a length of 32 bytes.  Secp256k1 public keys, in their compressed form, are 33 bytes.  The extra byte is either 0x02 or 0x03 depending on whether the y-value is odd or even.  This is a problem because some of our functions (eg: encryption using 'private-box') involve concatonating several keys to produce a shared secret.  If we have a mix of both key types, it is impossible to know when one ends and the other begins.

To overcome this, we propose that in 'private-box' messages, ed25519 public keys are prefixed with an additional byte, `0x00`.  This means that all public keys are now 33 bytes, and the first byte determines which crypto primative is used. 

The secp256k1-node module explicitly states that it is an experimental library.  We would naturally want to conduct a security audit before using this module in production.

## References:
- secret handshake paper
- https://davidederosa.com/basic-blockchain-programming/elliptic-curve-keys/
- [secp256ki article on bitcoin wiki](https://en.bitcoin.it/wiki/Secp256k1)
- [secp256k1 specification from the 'Standards for efficient cryptography group'](http://www.secg.org/sec2-v2.pdf)
- [A closer look at ethereum signatures - hackernoon](https://hackernoon.com/a-closer-look-at-ethereum-signatures-5784c14abecc) - quite interesting, shows how to verify signatures using solidity, amoung other things
[Generating a usable Ethereum wallet and its corresponding keys](https://kobl.one/blog/create-full-ethereum-keypair-and-address/) 
- Gavin Wood, ['Ethereum yellow paper'](http://gavwood.com/paper.pdf)

---

- [Generating a usable Ethereum wallet and its corresponding keys](https://kobl.one/blog/create-full-ethereum-keypair-and-address/) - this article I found really useful - it shows how to generate keys from the command line using OpenSSL.  Important to note - as illustrated in this article - there is an extra step to derive the eth address from the public key. This means that if ssb used secp256k1, ssb public keys would not be ethereum addresses - rather, ethereum addresses could be derived from them.  This process is documented in gavin wood's ethereum ['yellow paper'](http://gavwood.com/paper.pdf), and for bitcoin the relationship between public key and address is documented in [here](https://en.bitcoin.it/wiki/Technical_background_of_version_1_Bitcoin_addresses) and [here](https://en.bitcoin.it/wiki/Address)
- [stackexchange - what does secp256k1 look like?](https://bitcoin.stackexchange.com/questions/21907/what-does-the-curve-used-in-bitcoin-secp256k1-look-like) - i love these diagrams

