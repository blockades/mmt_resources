# Social Backups

![harmony](img/harmony.jpg)

I've been sketching out a few ideas for using #ssb as an encrypted secret sharing mechanism, basically a social password backup mechanism which we've been trialing in #mmt through the [coconut death roleplay](%IFRnSTlPvuxm7q97v4+ZTgDL7ypC9Q5y/nEVYu/xv1k=.sha256). 

Scoping out what this looks like has resulted in a few different ideas which, thanks to [@Piet](@U5GvOKP/YUza9k53DSXxT0mk3PIrnyAmessvNfZl5E0=.ed25519) and [@mix](@ye+QM09iPcDJD6YvQYjoQc7sLF/IFhmNbEqgdzQo3lQ=.ed25519)'s great and well explained Scuttlepoll code and my own slow, long and protracted learning from the last few months, I have begun to sketch out some schema's which illustrate the workflow and validate the data.

There are a few key concepts, of which [Invites & Responses](#1-invites-and-responses) could be really useful for other ssb features so I'm abstracting it into its own module.

## 1. [Invites and Responses](https://github.com/ssbc/scuttle-invite) 

This could be great for other future features in ssb. The concept already exists in [@happy0](@RJ09Kfs3neEZPrbpbWVDxkN92x9moe3aPusOMOc4S2I=.ed25519)'s `ssb-chess` and when I realised I was going to use a similar pattern, it made sense to build it as an abstraction. Utilises `root` and `branch` to point back to a relevant start link. 

Process is thus:

* Already exists within a context, the `root` link, such as an event, a process, a group, a game, etc.
* Alice sends Bob, Charlie, Dana, Eli and Fran an `invite`. Each receives an individual private message as `recps`.
* Bob, Dana and Fran accept, Eli declines, and Charlie is a bit forgetful and misses the deadline. Each returns a `response`, a private message, so Alice knows the response.
* Alice can now collate all consenting parties and initialize the process / event / group / game / etc.

## 2. Contract 

* Once sufficient responses have been returned, Alice collates all consenting parties and initializes a contract 
* The UI asks Alice for her secret, she enters it and selects a quorum of cosigners.
* Can either be totally private (only she can see) or includes the `recps` so they know who each other are and the details of the agreement (e.g. how many required to reassemble the password).
* the secret is not recorded in the database

## 3. Secrets

* Creation of the contract triggers a 'sharding' of Alice's secret and Bob, Dana and Fran each receive an encrypted message which Alice (and everyone else) cannot read. Alice knows who the recipients are due to the contract but can't see the secrets. Alice knows her secret is safe once gossiped.

## 4. Retrieval

* Haven't quite worked this out yet. Some or all of which may have to occur 'out-of-band', i.e. not within the framework.

Thoughts / suggestions and feedback on ssb code always helpful / useful :grinning:

#ssb-show-and-tell #ssb-learning 
