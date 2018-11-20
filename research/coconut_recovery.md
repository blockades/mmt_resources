
## Coconut Death

**What is Coconut Death?**

Coconut Death has become analagous to a speculative future whereby one or more of the MMT crowd get catatrophically hit on the head by a coconut falling from a tree thereby rendering them inert / incapacitated and unable to participate in signing group wallet transactions. We supposed that in the event of a multisignature wallet requiring 4/5 signatures to validate a transaction,with two signatories incapacitated by the dreaded coconut death, the rest of the team would be unable to easily sign a transaction move funds out of the now 'unstable' wallet. This is one of the reasons Dark Crystal emerged as a concept. If each team member shards their wallet seed and sends it to the other members of the group, it opens up the possibility for one of the two coconut dead members' seed to be recovered (in effect transforming the multisig into a 3/5), thus freeing up the locked funds in the wallet to the rest of the team.

In the context of an SSB identity, #coconutdeath can be analagous to:
1. Losing your Private Key, Backup or Device (the coconut lands on your laptop, shattering the motherboard and rendering your SSB identity inaccessible)
2. Having your device stolen (after having been hit over the head with a coconut by some sinister character)
3. Complete incapacitation or death (a coconut plummets from space and lands directly on you creating a crater the size of a small tropical island)

## Simulations

Peg and I conducted a roleplay experiment simulating the experience joining SSB as entirely new Scuttlebutt users, sharding our SSB identity using Dark Crystal, losing our computer, and reassembling.

### Scenario 1 - Loss of Private Key / Loss of Device

1. Person 1 (Identity A) loses their key and can no longer access SSB
2. Person 2 (Identity B) has a shard for Identity A sent by Person 1 via Dark Crystal
3. Person 2's shard message indicates it is in fact a shard of A's identity (as opposed to a different shard for a different key...)
4. Person 1 tells Person 2 that they've lost Identity A via a different communication protocol
5. Person 1 generates Identity C, a throwaway identity, and gets connected to Identity B via a pub (or an invite code?).
6. Person 2 receives assurance that the new identity received, Identity C, is infact Person 1 a.k.a Identity A.
7. Person 2 opens Dark Crystal and chooses to `Forward Shard`, selects the shard in question and is shown a form whereby they can select from a set of identites or input an identity string to forward the shard to.
8. Person 2 submits Identity C to the form.
9. Dark Crystal creates a new record, either `invite-reply` or a new message type `dark-crystal/forward` and sends the shard of Identity A to Identity C
10. Person 1 acting as Identity C receives a message from Person 2 (Identity B) that contains their shard.

**Thoughts:**

_Point 5:_
* When Person 1 generates their 'recovery' identity, Identity C, whats the minimum possible they can do to get connected to Identity B?
* Is it possible to do something similar to manyverse whereby an individual generates an invite code and shares it with Person 2 out-of-band. This exists in manyverse but I don't know if this is possible due to static home IPs, etc. @andrestaltz can you perhaps shed some light on this?
* The other option is to join the same pub as Identity C.

### Scenario 2 - Stolen Device
We didn't go to deep into this yet, suffice to say that I think its a similar scenario to 1, but we different action needs to be taken in terms of the interface to ensure the custodians behave correctly.

### Scenario 3 - Coconut Death 4 Realz
- How do the shard holders know who each-other are?
- They all know about a `root` message id. Each shard holder can do a shout out of `SHA2(root)`.
- Another shard holder can look around and assume that anyone who also shouts out a matching `SHA2(root)` has another piece of the puzzle, because they knew the `root`. Are there missing assumptions here? Can this be cheated? Sure someone can just copy that SHA hash and paste it into a message, thus fooling anyone else who is looking for that string.
- Any other ideas?

**Summary**
Much of my thoughts around this today are really UX related. 

The Dark Crystal interface really needs to separate user-flows and its narrative based on the differing scenarios / recovery strategies. For example, suppose rather than the simple case where peg's laptop gets smashed up by a falling cococnut, instead a giant walking cococnut robbed peg of his laptop (sorry peg!) and his identity with it. Supposing also that Peg has backed up both his Bitcoin private key and his SSB private key using that identity. When he comes to want to recover, the options to 'Return a Shard' and 'Forward a Shard' should not be in the same view. They could be easily mixed up and could result in a dramatic failure - rather than forwarding the old private key to the new SSB identity, peg's custodian sends the shard of the bitcoin private key back to the Coconut Robber. If a quorum of other shard holders makes the same mistake, then the bitcoin private key is revealed to the Robber.

The Dark Crystal interface doesn't at the moment allow a person to return a shard unless requested. But if the coconut robber has requested the bitcoin key shard back, it could easily be confused for forwarding the SSB key shard to a different identity. The interface really has to get a proper handle on this.

There's nothing about the interface at the moment that indicates precisely which shard the custodian should return. There needs to be somekind of metadata to indicate whether the identity is their SSB private key at the very least (which in effect acts as a master key to regain access to the other secret shards).

**Conclusion**

A scenario-based user-path as the interface is the better path. For example:

Dark Crystal app loads up and asks what what course of action you want to take.

1. Create a New Dark Crystal, Shard your secret and share it with some friends
2. A friend's lost their key? Send a secret shard back to its original owner 
3. A friend's lost their SSB identity or had their laptop stolen? Forward a secret shard to another identity

With pictures animating the process and text explanation we can ensure that people know exactly what they're doing and which is the correct option / scenario to choose. Lets treat this as an opportunity to teach people about how it works and narrate that through imagery. We can do the same on initial sync when scuttling after having joined a pub. Much like how Ubuntu or Windows shows pictures when you're installing the OS. Dark Crystal can show a series of images explaining the different scenarios. Much like how MyEtherWallet warns about security and how to use the wallet when you land on their homepage.

### Observations for Development

* Encrypt the `gossip.json` file with your ssb private key before sharding. Attach as a blob to the `dark-crystal/shard` message. Forward the `gossip.json` file when shard is returned to new identity. Once all shards are received, decrypt the gossip.json, inject into the incoming new `.ssb` folder with the new / old `secret` file, and switch identities. Wait for resync.
* We might want a new record (or could perhaps use `invite-reply` messages) called `dark-crystal/forward` that looks something like this:

```js
{ 
  key: "%...",
  value: {
    content: {
      type: "dark-crystal/forward",
      root: "%...",
      shard: "*=.box", // encrypt the shard sent back using the destination identity's public key (much like the same pattern we've already used)
      gossip: "&...", // blobId of gossip.json file
    }
  }
}
```

* Write a `flumeview-reduce` that listens for `dark-crystal/forward` messages. When one arrives, query for other `dark-crystal/forward` messages that have arrived, and using them attempt to reveal the secret. If the secret reveals successfully (we've essentially calculated the quorum), append to the reducer a record that contains a list of the IDs of the `dark-crystal/forward` messages, and the quorum required to reassemble. In the front-end, we have have a pull-stream setup which will check this reducer and allow the secret to be revealed if the relevant information is available to reveal. This could also expose a set of actions to perform:
  1. Delete current identity and rebuild original identity
  2. Backup current identity and rebuild original identity


### SSB Backlinks:

```
%IFRnSTlPvuxm7q97v4+ZTgDL7ypC9Q5y/nEVYu/xv1k=.sha256
%yWguHqHq0ZVs0ba2FVtyDaQLrUjwv9C0kUgi37pn35g=.sha256
%yAdCqJqI+ihjhCt6DGX9YBhtxujM9P9bwRAjVIZZvKo=.sha256
%FxK4GdAWVVEsWxn5Iz6nOlp2YM7TCm09zFwiojxphsw=.sha256
```
