
# Report on interoperability between the Ethereum and Secure Scuttlebutt networks

[link to doc on ethresear.ch](https://ethresear.ch/t/implementing-secp256k1-on-secure-scuttlebutt-ssb-to-create-cross-platform-ethereum-scuttlebutt-applications/4848)

## Introduction (TODO)

## Comparison of SSB with other off-chain protocols

Blockchains are suited to information where widespread consensus is critical, but due to the associated costs and limitations, it makes sense to use them as little as possible and have well-integrated off-chain systems. Ethereum is not simply a blockchain protocol but a stack of protocols including some which are designed specifically for off-chain transport and storage. So it makes sense to look at these protocols in order to establish whether SSB has something to offer which is not already there.

### Whisper

Whisper is a communication protocol with a focus on ephemeral messaging.  SSB however is designed to be a permanent log, although ephemeral messages can be sent over SSB using the module [SSB-ephemeral-keys](https://github.com/ssbc/ssb-ephemeral-keys).

Whisper messages include the recipient as metadata, meaning an external observer can see who is talking to who.  SSB-private obfuscates recipients, meaning an observer can see who is publishing encrypted messages, but not who they are being sent to.  This is only practical to do because of SSB's gossip protocol.  There is no ubiquitous view of the network, rather each peer can only access messages from a specified number of 'hops' away from their own node on the social graph. This means each peer has a small enough sub-set of the network that attempting to decrypt all messages because practical. This might seem like a lot of effort to go to just to obfuscate some metadata, but metadata leaking has been one of the biggest criticisms of traditional encrypted messaging approaches like PGP over email. 

- Eclipse attacks TODO

### Swarm

Swarm is a distributed storage platform and content distribution service. SSB also offerers distributed persistance, but it is not designed for content-heavy applications.  


- 'slow update times' like ipns

## Proposed approach

Lets consider two cases where interoperability between SSB and Ethereum would be useful:

1. You want to interact with some entity with a known Ethereum address using the Scuttlebutt protocol. Eg: by referencing in a Scuttlebutt message
2. You want to interact with some entity with a known Scuttlebutt feed id using the Ethereum protocol.  Eg: by sending them funds or including them in a smart contract. 

The problem is that the two systems use a different elliptic curve, so currently there can be no direct cryptographic relationship between an Ethereum address and an SSB feed id. SSB was designed to be cryptographic-primitive agnostic, so all feed ids and signatures have a suffix which describes them, typically '.ed25519', and similarly references to messages and blobs have a suffix describing their hash function. So we propose to introduce feed ids and signatures on the secp256k1 curve.

There is of course the difficulty of Diffie-Hellman encryption between keypairs on different curves. For this reason, we propose to only use secp256k1 keys for signing and have an associated curve25519 keypair for encryption.

However, it is worth noting that there could be a further use case for cross platform inter-operability where we didn't have this problem.  Suppose you want to use the Scuttlebutt protocol for off-chain communication using Ethereum accounts as identities, but were not interested in existing Scuttlebutt users, messages or infrastructure such as pubs.  Establishing a new SSB network where another curve is the norm would be not so difficult.  But for now, we assume that we need to design a system that allows for existing users to interact with users of the new cross-platform system. 

### EIP 712 - Ethereum typed structured data hashing and signing  

We propose to conform to EIP712, so that the same structured data reliably gives to same signature.

https://github.com/ethereum/EIPs/blob/master/EIPS/eip-712.md
https://medium.com/metamask/scaling-web3-with-signtypeddata-91d6efc8b290


## Current state of this project

- Key generation, seeded key generation, signing and verification are implemented and passing tests on our [fork of ssb-keys](https://github.com/blockades/ssb-keys) see also [further discussion in the initial pull request](https://github.com/blockades/ssb-keys/pull/1).
  
- The `.secp256k1` suffix for feedIds is allowed in our [fork of ssb-ref](https://github.com/blockades/ssb-ref)
- Some other experiments can be found in [this repo](https://github.com/blockades/secp_experiments)

Using these forked modules, we used TODO: add test code to a repo to publish some example messages to a test network. 

### Example message published with a secp256k1 feedId and signature:

```js
{ key: '%vtCIO56flJjvnokHmM0Fl2WXcITNaLV9RnQzTl7edyM=.sha256',
  value: 
   { previous: '%YFhNH3h97zkS/LTzo/EImAP9Nyl3KNBVxSI5HE77TBU=.sha256',
     sequence: 3,
     author: '@A8FGVdYR8q2yKeluGzE2+R0CTdFQXtzDa+jHRWE0SAqB.secp256k1',
     timestamp: 1549395437481,
     hash: 'sha256',
     content: 
      { type: 'post',
        text: 'it nice to be important but its more important to be nice' },
     signature: 'dg6qh+kvti0jCASiNRlF/iPO+oWsDjrsAmuTD2ZJtENlfJ3RH2bf5xbetF/kbsO+N3Al4YbCIohextle4bAa3w==.sig.secp256k1' },
  timestamp: 1549395437491 }
```


## Security issues

Implementing this could introduce a hoard of issues, but at this proof-of-concept level we have not prioritised this.  It is anyway worth noting the following: 

[secp256k1-node](https://github.com/cryptocoinjs/secp256k1-node) explicitly states in the readme that it is an experimental module.

To protect against the ['chosen protocol attack'](https://www.schneier.com/academic/paperfiles/paper-chosen-protocol.pdf), we don't want a valid SSB message to also be a valid Etherum transaction _ever_. In SSB this is addressed by using the `hmac_key` argument to `ssb-keys.signObj`. The idea is that there is a separate `hmac_key` for each type of thing which one is able to sign, and then `signObj(keys, hmac_key, obj)` is the same as `sign(keys, hmac(obj, hmac_key))`. This means it is almost impossible that `hmac(obj, hmac_key)` could also be a valid Ethereum transaction.

## Similar/complementary efforts

ConsenSys have begun implementing SSB in Java as part of their core library, Cava.  The idea is to make it interoperable with RLPx (the protocol with which Ethereum nodes operate with each other). 

## Possible alternative approaches

### Just having a 'this is my other key' message

Using the same keypair to sign SSB messages as well as blockchain transactions allows us to reliably refer to the same key holder on both systems.  But in the context of the current uses of the Ethereum and Scuttlebutt networks, there is also a disadvantage.  The security with which you safeguard a key to a wallet or smart contract is fundamentally different to the security required to safeguard a key for signing casual messages, and re-using keys for multiple purposes is often regarded as bad practice.  Using the same keypair for both would compromise security and/or introduce impractical conditions for sending SSB messages (having to enter passwords or requiring hardware devices).  A better option could be a way to look up and verify the associated addresses on both platforms. 

We could publish a public SSB message, of a particular message type so that it can easily be found, with a secp256k1 public key or Ethereum address.  This message could included signatures made with both the Ethereum key and the SSB key.  This would make it easy to, say, send funds via Ethereum to someone with a known SSB identity. Importantly, this could be done entirely in 'message space' with no protocol changes needed. Similarly, a message announcing an SSB feed id could be published to the Ethereum blockchain to allow the inverse - finding an SSB identity associated with a known SSB address.

### Multiple feeds using a single secure channel.

Another consideration is to have a single user or entity owning multiple SSB feeds, some which have different capabilities than others.  Imagine I have a 'normal' ed25519 SSB identity, which I use to establish a secure channel with peers by means of SSB's secret-handshake. I also have as second identity with some special property, such as signing with a secp256k1 key.  As the two feed-ids are 'friends', i am able to use the secure channel created by the first id, to replicate the second feed, meaning we don't have to worry about the handshake protocol working with both systems, or security issues with reusing keypairs for many purposes.

### `sameAs` 

`sameAs` is an SSB message type used to create links between SSB accounts such that a single identity can comprise of multiple accounts.  The primary use case is users with multiple devices, but it could be used to link accounts that have particular properties or abilities (such as signing on a different curve).

### 'blockparty'

[blockparty](https://github.com/blockparty-ssb/blockparty) is a multi-network SSB client which aims to create interoperability between different 'scuttleverses' (the 'main' scuttlebutt network has a particular network key, so there are many possible alternatives).  Taking this project as inspiration, we could have an alternative network where secp256k1 feed ids are the norm, but have some cross-references to the 'main' network, meaning we can make use of existing accounts and infrastructure such as pubs.
## Conclusion

We have implemented secp256k1 keys for signing, and allowing this on the main Scuttlebutt network is an obtainable goal, but greater clarity is needed on what exactly we want to make possible by doing so, as there are other solutions for cross-platform interoperability which don't require low level protocol changes.


### TODO:
- look at recieve-keys
- mention that we are using the keccak module, the same one as ethereumJS - we sign keccek256(message).
