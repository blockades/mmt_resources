
## Brainstorming coconut-related scenarios

### Loss of trust in one custodian

Suppose we loose trust in one person holding a shard.  This might be because they had their computer stolen.  Or maybe we had a really bad argument with them.  Or maybe we found out they weren't the person they were claiming to be.

In [Adi Shamir's original paper](https://cs.jhu.edu/~sdoshi/crypto/papers/shamirturing.pdf) he says that one of the great advantages of the scheme is that it is possible to create as many distinct sets of shards as you like without needing to modify the secret.  Each set of shards is incompatible with the other sets.  Using [Glenn Rempe's implementation](https://github.com/grempe/secrets.js), if we run the share method several times with the same secret, we get each time a different set of shards.  When generating a new set, an extra check could be done to rule out the extremely improbable case that an identical set had been generated. 

This means in a conventional (shards written on pieces of paper) secret sharing scenario, we could simply give new shards to the custodians we do still trust and ask them to destroy the old ones.  This would make the shard belonging to the untrusted person become useless. 

In our case, using the SSB immutable log, we have no way of destroying a message.  All we can do is issue a new set of shards for the same secret, and mark the old ones as not-to-be-used.

Although this is not as secure, I think it is worth implementing because there are other situations where such marks or tags would be useful.  Maybe a secret is no longer important (for example its a backup of an expired GPG key or a bitcoin wallet which no longer contains any funds), or maybe a mistake was made when entering the secret. 

### 100% Coconut dead

In this situation there are many things to consider.  How should the mechanism by which the custodians contact each other work?  Who should become the new secret holder?  What should they do with the secret.  For this is certainly worth bearing in mind, as [Pamela Morgan](https://medium.com/@pamelawjd) makes clear in 'Crypto-asset inheritance planning' that securely storing the secret solves only half of the problem.  We still need to know what to do with it.  Certain instructions could be included together with the secret.  But we need also to know under what circumstances should shards be recombined.

#### How to prove you are a custodian, and why might you want to

- One custodian, Alice, becomes aware that the secret holder, Bob, has been involved in a coconut accident.  Alice does not know the identities of the other custodians.  But she knows that Bob wants the secret to be recovered if the worst happens.
- Alice publishes a public SSB message, containing the hash of the rootId of the secret.
- On finding such a message, #dark-crystal compares that hash with the hashes of all rootIds that it knows about. 
- If one is found, the custodian sends a private message to Alice with the actual rootId to prove that they are also a custodian. 
- The custodians can then communicate about whether they all agree that Bob is really dead.
- As an extra security measure, Alice, the one who published the public message, is not allowed to become the new secret holder whom the others send the shards to.  This means there would be no motivation to initiate the recombining in order to get personal custody of the secret.  There would be no point in Alice pretending Bob is dead so she can get his secret, because she wont be the one getting their hands on the secret. 
- One of the other custodians publishes private invites requesting the shards.
- Alice and the other custodians respond and Bobs secret has a new owner. 

### The half way house to coconut death

Imagine the secret owner has lost their computer, and no longer has their SSB identity.  But they are still very much alive.  They would like to reconstruct a secret, but they no longer have the means to publish invites, nor to decrypt the shard messages.  

They go to one of the custodians, Carol, and explain what has happened and give her the identities of the others custodians.  In this case there's no need for Carol to publish a public message, she can just send requests for shards, but somehow all custodians must agree that the secret owner has given their consent.

We also have a second problem.  Remember that the secret owner lost their computer.  Once they have got their secret back they will probably also want to mark the shards as not-to-be-used. 

## Other possible dark-crystal features

### Sharing larger secrets 

SSB messages have a size limit, and the secrets library we are using means that shards are 4 times the size of the secret.  For larger secrets, it would make sense to encrypt them with some symmetric encryption tool, place them somewhere accessible, and shard only the encryption key.

- [SSB blobs](https://github.com/ssbc/ssb-blobs) could be used for this.  Worth noting that the default maximum blob size is 5mb. Other than that I don't know too much about how they works but i would like to read up on it.
- Otherwise some other content addressable distributed storage such as [DAT](https://datproject.org/) could be used. 
- [tomb](https://www.dyne.org/software/tomb/) keys are usually around 850 bytes, so should be small enough that the shards fit in an ssb message.

### Support for sharing shards by other means than SSB

I would really like to have the option to send some shards without using SSB, and include a QR code generator.  So you can print one for your grandmother's sock drawer as well as your SSB buddies. 

Taking this a step further,  Nikolai suggested that we build a multi-network application, as in you can send some shards via SSB, others on say keybase, others by GPG encrypted email, others on paper.  So it doesn't matter what your friends use, dark-crystal would cover all bases.  While this sounds to me pretty impractical to implement and a nightmare to maintain, it would mean a lot more diversity of funding sources for us.
