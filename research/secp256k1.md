
## On using secp256k1 keys on ssb

Listing here a few links on this topic that i was reading up on.

ssb backlinks:
- 'thoughts about adding new signing key types' (dominic) - pasted below 
- aljoscha's response is definately worth reading as they are somewhat critical and demand an explanation why this might be needed %6xDjaCQ1DIDvhIxqulZ6JsvxDp2LkYX/tvGWv1HL68g=.sha256
- 'group multisig, & same-as but with people' (dominic) %D0tue88kaAOdZL7zuBbmRZUF70rBYDvnPZbE+Vd4jwQ=.sha25

Web:
- [secp256ki article on bitcoin wiki](https://en.bitcoin.it/wiki/Secp256k1)
- [specification from the 'Standards for efficient cryptography group'](http://www.secg.org/sec2-v2.pdf)
- [A closer look at ethereum signatures - hackernoon](https://hackernoon.com/a-closer-look-at-ethereum-signatures-5784c14abecc) - quite interesting, shows how to verify signatures using solidity, amoung other things
- [A reddit thread where vitalik hints that ethereum are considering ed25519 keys](https://www.reddit.com/r/ethereum/comments/30k4ry/elliptic_curve_choices_in_ethereum_secp256k1_vs/) - from 3 years ago and i cant find a better reference... but this would mean ssb keys would already be using the same curve as ethereum keys. 
- [Generating a usable Ethereum wallet and its corresponding keys](https://kobl.one/blog/create-full-ethereum-keypair-and-address/) - this article I found really useful - it shows how to generate keys from the command line using OpenSSL.  Important to note - as illustrated in this article - there is an extra step to derive the eth address from the public key. This means that if ssb used secp256k1, ssb public keys would not be ethereum addresses - rather, ethereum addresses could be derived from them.  This process is documented in gavin wood's ethereum ['yellow paper'](http://gavwood.com/paper.pdf), and for bitcoin the relationship between public key and address is documented in [here](https://en.bitcoin.it/wiki/Technical_background_of_version_1_Bitcoin_addresses) and [here](https://en.bitcoin.it/wiki/Address)
- [stackexchange - what does secp256k1 look like?](https://bitcoin.stackexchange.com/questions/21907/what-does-the-curve-used-in-bitcoin-secp256k1-look-like) - i love these diagrams

Whats missing for me is a bit of imagination as to what implications this would have - what could you really do with this that you cant do right now?

and secondly, more importantly, *do people want this*?  Asides from security/implementation concerns, what are the arguments against?  I guess this could be seen as a sort of bridge between the scuttleverse and the crypto/blockchain world.  Is that something people want?

---

## thoughts about adding new signing key types (by Dominic)

Currently signing keys and identities are ed25519 keys as provided by the sodium library.
there are two candidates for additional algorithms. `secp256k1` as used in ethereum and bitcoin,
and `bls` as will be used in dfinity which has [interesting group signature properties](%D0tue88kaAOdZL7zuBbmRZUF70rBYDvnPZbE+Vd4jwQ=.sha256). `secp256k1` is just a marketing bullet point, although I'm sure it will be a big deal for some, but `bls` enables a really interesting new feature, however the awesome part is that bls group signatures are exactly the same as ordinary signatures, so if we implement support for ordinary bls signatures, we can implement the cool group stuff later.

Heres what I think needs to happen:

* There are _lots_ of modules that use `ssb-ref` to check whether some string is a ssb type (message, feed, blob). We could change all of those modules to call something on sbot... or we could just add a function to `ssb-ref` to accept additional extentions, something like `ref.allowFeedExtention('secp256k1')` and then `@blah...blah.secp256k1` is now a valid feed id.
* `ssb-validate` would need to be refactored out a bit so that you can have custom validation for different key types... or is it just the signature that needs to change?

That really seems quite simple.

---

Adjacent thought: perhaps the most embarrassing quirk in the signing format is that the hash takes the `latin1` string of the json. This is a bug we inherited from old node.js which used 'binary' as the default string encoding for `Hash.update(str)` - although everything else used utf8! This is not actually a security problem, but it is silly. Also the max length is actually the utf8 count, not the byte length. If it was all the longest utf8 chars, a message could approach 32k!

What I'm thinking: the hash field, which is currently hard coded to "sha256" could be "utf8.sha256". If it's set to that, then the json is properly converted to a buffer, and then hash taken from that.

I'm thinking that '.utf8.' _doesn't_ need to be part of the message id, just the hash field.
utf8 doesn't matter until you actually get the message. Fixing this would actually be easier if you left it out of the hash.

* when you generate the id of a `hash: "utf8.sha256"` message, convert it to utf8 properly. add code to do this, but continue creating messages with hash `sha256`, until you are sure everyone has the new code, and then switch to creating the new style messages. It's actually only a couple of line to change, but probably roll out the second part several months later.

---

btw, I think this isn't actually that difficult! It wouldn't be too complicated because it doesn't involve changing many parts of ssb, or any non-backwards compatible changes. I'd be very happy to advise someone who wanted to work on this!
