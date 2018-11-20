# minimal coconut

In figuring our the minimal scenarios we want to cover I want to reason about whats **non-negotiable** and what's **nice to have** (and that we could perhaps design and build for later).

I'm gonna give the excellently described scenarios [here](%W5tFGtKQwXQzyXwqIc54nuK9T0zDqlFQjE0YpS9bAq8=.sha256) shorter names so I can talk more easily

0. **happy** - the situation we have already built for
1. **swim** - as in your laptop went for a swim (nee _loss of device / private key_) 
2. **theft** - a bad actor has access to your private key (nee _stolen device_)
3. **inheritance** - I am totally gone, it's up to those I've left things to (nee _coconut death for realz_)

---

## proposal: solve for _theft_

Here's a breakdown of why I think that's the case.

If we are missing our laptop, then the safe thing to do is assume the _theft_ case (and that your identity is comprimised).

There are 2 ways you could recover your crystals if _theft_ has happened: 
- a) recover your ssb key, then request your shards
- b) ask for your shards to be **forwarded** to a new identity

Option (a) is not a useful option because even if you recover your scuttlebutt identity, requesting your shards back is dangerous (if you don't fork your feed in doing it, then you'll be giving your crystals to a bad actor). (_crystal_ is synonomous with the fixed crystal made up of all the shards, i.e. some backed up secret)

So, I think we need to focus exclusively on shard fwd'ing. (and not at all one recovering a scuttlebutt identity for our purposes)

I think we can leave the _inheritence_ case, because I feel the solution is going to be fairly similar to the _theft_ case (fwding shards) ... and I think we can extend to that nicely. In contrast the _swim_ solution (resurect the identity) could be extended to solve _inheritence_, but would give your inheritor access to everything private you've said (this is something awkward pointed out in the Crypto Inheritence guide which I think we should just avoid)

---

## 0. happy path

**Protagonist**
```
have secret
  └─> shards secret 
      └─> ... recovers secret (v1 done)
```

**Custodian**
```
receive a shard
  ├─> gets gets request to return shard
  │   └─> returns shard (v1 done)
  └─> returns shard
```


## 1. ~~swim~~

Not handling this at this stage

## 2. theft

**Protagonist**
```
laptop goes missing
  ├─> asks friends to "tombstone" old account (optional)
  └─> makes a new account
      ├─> attests new account is "reincarnation" of original
      └─> requests all shards fwdd
          └─> recovers secrets 
              └─> updates secrets, creates new shards (happy path again)
```

**Attester**
```
protagonist contacts you out of band about stolen laptop
  ├─> you mark their account as "stolen"
  └─> you define a "reincarnation" (pointing from read account to the reborn)

you see supicious activity from the protaginists account
  └─> you mark their account as "suspicious: stolen"

someone tries to trick you into thinking the Protaginist account has been stolen
  ├─> you mark the account as "still valid"
  └─> you mark the trickster as "suspicious: phisher"
```

**Custodian**
```
(include: all the Attester paths)

you see protaginist's account has been marked "stolen" (you care cos you hold shards)
  └─> have to make counter attestation before able to return shards (?)

receives a request to fwd all of Protagonist's shards
  └─> you check the two identities, communicate with the Protagonist, and make an attestation
      ├─> fwds shards
      └─> don't fwd shards

you know a the Protagonist account is gone, and know new account
  ├─> fwds shards 
  ├─> attest a "reincarnation"
  │   └─> fwds shards
  └─> attest a "reincarnation" **privately**
      └─> fwds shards
```

