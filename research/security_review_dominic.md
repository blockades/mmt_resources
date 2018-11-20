## security review of dark-crystal

forked from Dev Diary 02.11.2018 / Coconut Death

I started by doing a quick search for known vulnerabilities,  found some [vulnerabilities in SSS described on this page](https://ericrafaloff.com/shamirs-secret-sharing-scheme/) and also this paper: [how _not_ to share a secret](https://arxiv.org/pdf/1001.1877.pdf) (I didn't bother to try understand all the math, just using it for hints)

1. small metadata leak: length of the secret is revealed (solution: pad the secret)
2. possible for participant to return the wrong share, which means the correct secret is not recovered.
3. If the secret isn't very strong, like "password", it may be possible to confirm a guess just using a single share.
4. If two different shares have some relation (such as one being a known multiple of the other) then the other secret can be derived from the first.

Note: the last two are partly me reading between the lines of that paper, which I quickly skimmed. I'm not staking my reputation on those being true, by the following suggestions I have will cover this _just in case_ they are true. Better safe than sorry.

`dark-crystal` is a key building block for ssb applications, and I believe, usable security applications in general. We want it to be _rock solid_, so that it does exactly what it says on the tin and _you do not have to understand internal details in order to use it safely_. This last point is extremely important and I'd be disapointed if any ssb crypto did not have this property.

Most of the above problems can be fixed using a layer of symmetric crypto. As I suggested in the forked-from thread, sharing a random key, and using that to symmetrically encrypt the actual secret. too-long secrets is currently a problem, but encrypting the secret symmetrically does not have much overhead - 16 additional bytes for the mac + the secret size, and the size of the share will always be the same.

```
key = randomBytes(32)
shares = createShares(key, N, threashold).map(function (share) {
  //give each share a different encryption, also makes it not obvious two shares are for the
  //same secret. it's okay to use the same key again if the nonce is different, so we use
  //the hash of the share.
  return share + secretbox(secret, key, hash(share))
})
```

Metadata - problem 1, this is not really a very big problem, regular ssb messages private messages don't hide the length. if you wanted could instead have the encrypted secret be between the true size and twice that size. `secretbox([secret.length, secret, randomBytes(secret.length*random())`

The library used left-pads the secret to be shared with ascii zeros then "1" then the secret,
so that it's possible to distinguish between padding and secret. Since it's padded with zeros,
this protects against metadata (1) but not against 3 (confirming a guess at bad secret) since it doesn't increase the entropy. It would be much better to pad with random data.

But, we should first consider 3, and 4 - problems where mathematical properties of the secret leaks through. problems like this are typical of number theory based cryptography. 3 (weak secret) is easily fixed by sharing a known strong secret (one the system has generated, not one the user has provided). This also prevents 4 (interaction between mathematically related secrets)

One problem that dark-crystal currently has, is that it does not store the current quorum size, which means when reconstructing the secret you need some way to detect whether you've got it. this is mentioned in ["possible enhancements"](https://github.com/grempe/secrets.js#possible-future-enhancements) section of the library. Using libsodium's `secretbox` solves this problem, because a mac is attached to the secret, so it either returns the plaintext or fails.

Based on my current understanding of secret sharing (this morning's work) that may mitigate problem 3 (note: in a security context "mitigate" means _reduce a risk_ or _make a problem less bad_, _remediate_ means _remove the problem entirely_). meaning if you have a k/N secret, and 1 peer returns the wrong secret, it won't open with k/N, but if you get another honest share (now you have k+1 shares) you can just try k times, excluding each share until you successfully decrypt.

Remembering the secret has two parts - the shamir share, and the symmetric part. As long as one peer returns the correct symmetric part, you will be able to decrypt that. As long as you have k/N shamir shares. For any k, trying to combine every k-1 ... 1 possibilities will not be a scalability problem because the order of the shares does not matter.

Okay, I'm gonna look at the paper on authenticated sharing and see if that is better...

---

update: [shamir secret sharing is post quantum](https://crypto.stackexchange.com/questions/10904/post-quantum-threshold-secret-sharing) that's good news, and I now suspect that 3 (weak password) probably isn't a problem.

Hmm, the paper I read [how-not-to-share-a-secret.pdf](&5hLPr170ZXr94s4hPFSxAFUA1Jv4IkninrktmbnXy7Q=.sha256) is actually about a different scheme to shamir's, that seems to allow sharing multiple sets of secrets at once.

reading _Detection and identification of cheaters in (t,n) secret sharing scheme_ [detection-of-cheaters-in-sss.pdf](&ImMVDU3+1qm+0WWnpJnFUnG08wYE2CXK+ABAKgiOB+Y=.sha256)

outlines 3 attacks/problems

1. a peer returns an incorrect share by accident (for example, because of a bug)
2. malicious peers generating incorrect shares, but without having the chance to see any honest shares first.
3. as in 2, except attackers have the chance to see what honest peers reveal first.

3 is obviously a lower bar (thus easier to attack than 2) and is also more relevant to dark-crystal.

Hmm, okay I don't fully understand this paper (too many cryptic math symbols) but they claim they detect cheating in `O(1)` and detect who the cheat is in `O(j!)` (I think j is the number of cheaters). j factorial is pretty big, but okay since j is small. It's the same as my suggestion would be though. (I need to look at this more though)

---

## revoking trust - deleting shares

in my research, I also encountered the idea of [renewed shares](https://en.wikipedia.org/wiki/Secret_sharing#Proactive_secret_sharing). This allows you to remove someone from the set of shares. I strongly recommend that `dark-crystal` adds this to the roadmap.

Trust is not a permanent state - I think it is important that if you can give trust you can also take it back easily. For example - say you share something with your partner - but then go through a difficult breakup - maybe you'd want your security to not depend on them anymore. Another example - one of your shares looses their device -- possibly stolen. Now a potential attacker has one share.

Solution: update the rest of the shares (any maybe add a new peer). If the peers delete then gets hold of one of the new shares, well it cannot be combined with any of the old shares! So the attacker has to acquire a quorum of shares before anyone suspects anything.

The neat thing here when you revoke trust in a share, that share holder doesn't have to do anything. Instead, the share holders you still trust replace the share, and that is enough!

Since ssb is on the record, we can't directly delete shares - but we can if we encrypt them to an ephemeral key.

Something like this:

Alice sends a request to Bob, "hi Bob, can you look after a secret share for me?"
Bob replies "yes, encrypt it to this ephemeral public key `bob_e`". Bob's stores this key on disk, for now. 
Alice also generates an ephemeral key, `alice_e` and encrypts the share, sending bob `alice_e.public, secretbox(share_bob, alice_e*bob_e)` then deletes `alice_e`'s private key. (note: alice sends the public key she used to bob, he'll need that to decrypt the share)

Later, she wants to update the share - she sends a message to bob: "please delete that share" and bob deletes his ephemeral key. Now bob can't decrypt that share anymore! So if an attacker gets a hold of bob's device, they won't have that share either.

If bob sent an array of ephemeral keys, then alice could update the share that many times without having to do another round trip.

PS. you'd better also look into how to securely delete files. I think this might depend on the underlying storage architecture sometimes. Or it might be as easy as just writing 0's over the file.

---

## notes: how a secret is sharded and returned

A _primary_ peer creates shard messages for all _holders_. each shard message is encrypted to the _holder_ and the _primary_,
but then the shard inside of that is again encrypted only to the _holder_. _This means the primary forgets the shards._
You can decrypt the outer (and so see who you sent shards too) but not regain the shard.

*** following key compromise, compromiser knowns who holds shards *** (this may be considered necessary...)

When you request the shards back, a private request is sent to each holder. They then decrypt the shard from the previous message, and then send it back. https://github.com/blockades/scuttle-dark-crystal/blob/master/recover/async/reply.js#L61-L62

```
{
  root, branch, accept: true,
  body: decrypted_shard,
  recps: [primary, holder]
}
```

The shard is decrypted and sent back to the primary. the holder does not forget the shard. **future key compromise of a qorum of holders can recover the secret**

But worse: the shards are now on permanent logs encrypted to the primary - so **after recovery, future compromise of the holder can recover the secret**. However, key compromise before recovery _does not_ reveal the secret, but after recovery _it does_.

It seems unfortunate that dark-crystal goes to a special effort to avoid logging the shards, but then looses that property after recovery. In particular, for backing up a cryptocurrency private key, it would be better not to have that private key on the log.

**mitigation**: with current design, a dark-crystal user should move all funds from the recovered wallet to a new address after recovery. However, this is not obvious and they'll probably forget.

**remediation**: [internal forward-secrecy](%eYqUfFjpI7Lcru8CLEHxTuML/nbNUz/BL9R72P6CYHc=.sha256) as suggested above for revoking trust would also fix this problem.

("mitigation" and "remediation" are auditing terms - mitigation is what users can currently do to reduce or avoid the problem, "remediation" is how the problem can be fixed by a change to the system)
