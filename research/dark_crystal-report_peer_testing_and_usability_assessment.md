<p align="center">
  <img src="./img/dark-crystal-icon_200x200.png" alt="dark-crystal-icon" width="200" height="200" style="padding-bottom: 0.5em;" />
</p>

# Dark Crystal

## Peer Testing and Usability Assessment

### Summary

Peer testing was undertaken by members of the Dark Crystal team through individual and group sessions at multiple meetups and events across a period of two months. Much of the feedback opinions and data was collected at the [Simply Secure design residency in Berlin](https://simplysecure.org/underexposed/) in January 2019, at [Agorama Sever Coop in London](https://home.agorama.org.uk/) in February 2019 and at Art Hack in Wellington, NZ in January 2019.

Dark Crystal's strengths currently lie in a very clear conceptualisation of the process of sharing secrets among trusted peers. Once peers had explored the application and gained a knowledge of the context in which to apply make use of it, the nuance of this analogy was widely appreciated and most people interacted fairly intuitively with the application. Overall we received a lot of excitement about the project and its stated goals, and there was significant enthusiasm about the implementation so far.

There were however several significant UX barriers to adoption by peers, both within the scuttlebutt community and for new peers arriving via the website. The most important areas identified are:

* The use of language as a possible barrier to entry
* The onboarding challenges that the Scuttlebutt community already faces
* The lack of clear naming of certain functions and actions
* The lack of an integrated tutorial or guide on what it does and how to use it
* The lack of clear explanation of what data is public and what data is private

There remains an embedded assumption about how peer-to-peer (p2p) applications, specifically scuttlebutt, work. For new peers with little prior knowledge of p2p and/or scuttlebutt, the application fails to indicate what the preconditions are to ensuring your data sends effectively.

### Methodology

- Little to no knowledge of the underlying network and data persistence protocol Scuttlebutt was assumed.
- Peers were given as little prior information possible in an attempt to simulate a new peer arriving in the application following installation from the website.
- Peers were asked to read the website at [darkcrystal.pw](https://darkcrystal.pw) and gain an understanding of the problem that Dark Crystal was attempting to address.
- Peers were either asked to install Patchbay and navigate to the `/dark-crystal` section of the application to begin to interact with the interface.
- Peers were questioned about what they were drawn towards as they interacted with the application, and what they expected certain actions to do.
- Peers were questioned about what they understood the messages written in the interface to mean and how that mapped onto their understanding of the application gained from the website.

---

### Points for Discussion

There is no hierarchy or particular order of importance.

1. [Language](#language)
2. [Naming](#naming)
3. [Onboarding](#onboarding)
4. [Privacy transparency](#privacy-transparency)
5. [Behaviour and Navigation](#behaviour-and-navigation)
6. [Delivery confirmation](#delivery-confirmation)
7. [Push or Pull](#push-or-pull)
8. [Consent](#consent)

#### Language
During the ideation phase of Dark Crystal, it was helpful to map the language of magic onto the social protocol as a device to conceptualise the process of sharing within a trusting group of peers, much akin to a coven converging to perform a ritual and parting their separate ways after the spell had been cast. Through the development process, this lanaguage was placed into the UI.

Several peers expressed that the metaphors used within the application were confusing and obfuscating of the underlying operations of the application. This is a highly subjective perspective, some may find the language engaging, others may find it alienating. What is important to note is that since Dark Crystal is about providing accessibility to cryptography and secure and sovereign messaging to a broad base of peers, most specifically enabling peers on the margins of society to engage, this 'cliqueyness' could work contrary to the intention of the application. This deserves further examination and deeper research into specific target communities.

All peers found the tab mappings of 'My Crystals', 'Others Shards' and 'Others Crystals' to be highly confusing and left much to be explained as to what exactly the data they were looking at actually was.

Peers were generally enthusiastic about the use of 'crystals' and 'shards' to conceptualise the process / protocol. However multiple mixed messages in the language and iconography used in the application raised concerns. Many felt there was not a clear enough definition as to what exactly a 'crystal' and a 'shard' referred to in the interface. This was compounded by the use of a crystal icon as both an indicator of a 'shard' in the 'Others Shards' section, as well as their use to represent a reformed 'crystal' in the 'Others Crystals' section.

#### Naming
One peer was confused as to what the `secret` field suggested, whether this was some kind of extra cipher input to doubly secure your SSB key. Once it was explained that the secret could be any string, they they attempted to paste and entire document in and came up against the byte limitation.

The difference between the `name` and the `label` fields is not clear at all, with one peer aliking them to `title` and `description` as typical fields in a form. `name` and `label` are overlapping concepts. `label` could also imply tags.

There is nothing to suggest that the `name` is only something you see and remains outside of the secret, while the `label` is packaged up within the secret. Once it was explained to the peer who raised this, and it's what its intention was there as, the peer in question expressed that they felt this was an unclear and possibly one-to-many mapping of 'purpose' and 'concept', that the packaging of the label into the secret when sharded actually revealed that there were two concepts attempting to fulfil the same purpose, and that label was they felt a redundant concept, since there is nothing to stop you from putting the information from the label into the secret. This deserves further thought and discussion.

Many peers trialing the application were unsure what the 'request' button would do. It was explained that this would send a message asking for the return of the shard, and that this (rather than an automated response) was a necessary hurdle to prevent someone from using a lost or stolen device to steal all the secrets, thereby rendering the application useless. After this explanation, it made sense, though the prominence of the button alongside little to no context seemed unintuitive and unclear. The modal that flashes up with a warning asking 'Are you sure' as a part of that process was off putting enough to prevent peers from pressing the request button without being sure. But since there was no clear explanation of what the request would actually do, it rendered the functionality somewhat pointless. Several peers would only press the button after being reassured what it would do. Others were more gung-ho and pressed it to see what happened.

Other peers raised whether naming a secret would actually work for some people. Whether this can be directly addressed or whether this is simply 'peer error' is up to debate. While Dark Crystal should aspire to make things as intuitive as possible, there is only so much you can hold someone's hand. This is worth testing over a long period. Its possible the UI should suggest a naming convention to people as a guideline to work with, then people can apply with what makes sense for them.

#### Onboarding
The onboarding issues for Scuttlebutt itself are well known but need restating in the context of Dark Crystal's usability. Due to it currently being embedded within Patchbay, and sharing Patchbay indexes that aren't currently required by Dark Crystal, this causes a significant delay when starting the application for the first time, and when listening for the arrival of new data. At times this meant a peer signing up to try out Dark Crystal had to wait **20 minutes** for data to sync and Dark Crystal to be usable. While encouraging people to be patient why trying out prototype technolgy is awkward but relatively acceptable, in order to achieve wide peer-base, the waiting times are simply unacceptable and are a sure fire way to lose new peers.

In some instances, it took several hours for shards to render in the application between certain peers (or they never did), despite being local peers on the same network. It is not clear whether they have 'arrived' in the local database and just haven't indexed, or whether there was a network transmission failure. While Scuttlebutt is 99 times out of 100 reliable (if not more so), if we cannot guarantee delivery of shards, this remains a significant and possibly killer issue. More research needs to be done on the lower level implementation of Scuttlebot to ensure messages are gossiped and / or indexed correctly.

#### Privacy Transparency
There are currently no clear indicators or assurances in the client that the data is actually encrypted and private, and the interface makes the assumption that peers using the application already possess that knowledge.

Many peers expressed a desire for reassurance, at least when initially becoming familiar with the application, that the information contained in the application is either encrypted to yourself only, or in the case of the shards of the secret, encrypted and sent to the destination peers.

Due to the social nature of scuttlebutt, and the secure nature of Dark Crystal, its incredibly important to strike a clear distinction between what is public and what is private.

#### Behaviour and Navigation

Some peers found both the interface and the protocol puzzling and expressed this confusion in the form of questions such as:

> How did I get here?
> Where am I currently?
> Where am I going next?
> What is going to happen next?
> What happens if I click this?
> Will I be able to go backwards?
> Will I be able to change my mind?
> How many steps will there be in this process?
> Have I done this right?

Such questions reveal an inability to easily intuit what the consequences of a specific action might be. This has serious ramifications for Dark Crystal which is fundamentally about handling sensitive information.

Some peers observered they felt the UI was actively encouraging them to share their secrets. This could be problematic.

Several peers expected different behaviour when hitting the `ESC` button when selecting a custodian, expecting it to simply close the dropdown rather than exit the form modal.

Multiple peers reported unintuitive use of anchor elements throughout the application, here is one such example:

> On the main page of DC, I clicked on the image of the person who had sent me a shard.
> I expected to it to take me to the details of the shard.
> Instead it took me to their profile.

A bug that persisted in the custodian suggester has been fixed. This was an early behavioural issue that has been resolved.

There is no importance hierarchy in New Crystal form. Peers reinforced our belief that a flat form with no additional information (such as tooltips) meant it was not visually clear what was of importance.

#### Delivery Confirmation

Once the shards have been 'sent', peers who were aware of the underlying mechanism of scuttlebutt questioned whether this was an honest statement. While the messages may have published to your local log / database, this does not mean that the messages have left the source computer.

Peers stated that this was misleading and / or obfuscating of reality. There is no guarantee the shard has actually left your computer and this inevitably would prove to be problematic.

Peers expressed a desire for, at the bare minimum, some kind of sync indicator to be shown when disconnected from other peers / offline in order to ensure that the app doesn't mislead you into believing a shard has left your computer when it actually hasn't.

Peers also expressed a desire for a confirmation that the shard has been delivered _and received_.

#### Push or Pull?
One peer suggested Dark Crystal lends itself more strongly to push notifications, rather than pull-based notifications.

In the case where a request has been sent for a shard to be returned to the originator, there is no clear indicator to the shard custodian that a request has arrived. The custodian must go searching for this information. While this was conceived of by the developers as as a strength (the onus is on the originator of the secret to actively contact their custodians to request the return of the shard), to one peer this seemed counter-intuitive.

This peer stated that due to the importance of the request, it makes sense that the custodians are notified immediately that their trusted contact is in need of their secret. Its a clear indicator to trusted contacts that either the request is genuine, or the identity of the secret originator has been compromised. In both cases it is possibly better for all parties involved to be notified of this sooner rather than later. This approach has merit. Technically it needs further consideration by the team as it runs counter to the 'pull-based' nature of Scuttlebutt.

#### Consent

Several peers raised the issue that currently there is no consent mechanism whereby a potential custodian of the shard can be asked if they want to actually are willing to be a custodian.

In a [recent podcast](https://keybase.pub/danielsan/the-local-gossip/the-local-gossip-NeB4q4Hy-8-dark-crystal-diaries-0-cory-doctorow/) about Dark Crystal, Cory Doctorow raised a possible threat model that the project faces, whereby those that are implicated in being custodians of a secret are potentially under threat from an attacker seeking to reveal that secret. This is incredibly problematic if the custodian is not a willing party in this arrangement. A clear consent mechanism is an important / necessary feature in order to ensure this application behaves up to the ethical standard to which we hold ourselves and doesn't implicate people unknowingly or unwillingly into potentially dangerous situations.

This has been a discussion throughout the process and the team is well aware of consent as a core component of the application. It was screened out in the initial implementation as it was felt by the team that it was more important to build a working prototype, and the mechanism for obtaining consent warranted further research and discussion.

---

### Feature Requests / Suggestions as 'Peer Journeys'
This list includes as many suggestions that could be turned into peer journeys. While some are great suggestions, others may be less relevant / applicable, and some may be too much of a design change to consider implementing in the application in its current form. Its up to us as a team to decide what we should keep and what we should throw away.

- As a peer, it would be helpful to receive a push notification stating that a request to return a shard has been received, along with a text alert to  contact the secret originator, in order to check that this request was authentic / valid.

- As a peer, I would like to see a 'sync' indicator that tells me when messages I have published have connected to at least one other peer in the network, so that I know that the data has been sent has left my computer.
  * Watch the relevant messages in the SSB database 
  * Inform the client application when they have left the source computer

- As a peer, I would like to receive an indicator that shards that I have sent to my peers have been received, so that I am safe in the knowledge that my secret is safe.
  * Ask the destination computer / peer to automatically publish a response after the shard has been indexed.
  * This could be as simple as a flume plugin that publishes a private reverse message for each shard message received.

- As a peer, when I first start the application, I would like to receive the option to have a guided tutorial of the interface, explaining the total functionality of the app, and how to use it safely.

- As a peer, I would like to be able to navigate to a 'help' section where I can view a clear set of instructions on how to use the application.

- As a peer, when I go to the help page, I would like to retoggle the guided tutorial and watch it again.

- As a peer, I would like to be able to navigate to somewhere in the application where there is a clear introduction or guide on how to use this application.

- As a peer, when creating a new dark crystal, I would like to use a slider to indicate the quorum. This is a visually intuitive way of preventing me from choosing a quorum of 1 (which is invalid).
  * Guarantees that a peer can _never_ choose a higher quorum than the number of custodians
  * As a peer, when I select 2 or more custodians, a slider appears below which enables me to indicate the desired quorum.

- As a peer, when moving the quorum slider or changing the number of custodians, I would like a visual indicator to dynamically show my the level of trust this quorum / number of custodians implies.
  * A 'trust indicator', much like a password strength indicator, would be a great addition to the interface to help peers visualise the trust band they are invoking.
  * This could adapt dynamically as the numbers are changed to illustrate varying bands of trust.
  * 'Bands of Trust' could also be explained clearly in the application and on our website, and indicated again here.
  * A clear banded system of trust would be a really positive addition to the application. In effect, a trust 'standard'.

- As a peer, which completing the new crystal form, I should only see the 'submit' button when I have completed all the necessary fields.

- As a peer, I would like to be able to revoke a shard from a person I no longer trust.

- As a peer, when I navigate to my list of Dark Crystals, I would like a mechanism to sort of filter my secrets

- As a peer, when I create a new crystal, rather than giving them a name, I would like to give them a list of tags, so that I can categorise / intuit their purpose more easily.

- As a peer, I would like to enter a master password which gives me access to the client application and the underlying database. This is so that I can use a memorable passphrase to ensure my data is properly encrypted.
  * Sadly people aren't encouraged / bothered to setup full disk encryption, especially with Windows machines, and many people don't even have a password to their computers.
  * Practically speaking it is possible, but a pain to implement as it has broader ramifications for the entire scuttlebutt ecosystem and other client applications as it regulates access to the database.
  * This could be a separate application that is run on start-up before any scuttlebutt client is allowed to boot, and is called as a hook when all scuttlebutt client applications close.

- As a peer, when I create a new crystal, I would like to choose the same person twice in order to give that person more trust.
  * Practically speaking, giving one person two shards in effect lowers the quorum for that person. Interestingly, it doesn't do the same for the others. A neat suggestion!
  * Could this be weaved into the 'trust indicator' feature to map out a visualisation of trust down to the level of the individuals involved?

---

#### Bugs
- A quorum of 1 triggers cascading errors in Patchbay and it requires you to refresh the application.

---

## Notes:
In order to rid the tech-world of the 'peer' concept, this document substitutes the word 'peer' for 'peer'.

---

## Thanks

_A huge thank you to [Simply Secure](https://simplysecure.org/), [Agorama Server Coop](https://home.agorama.org.uk/), Art Hack, and all the individuals from the Scuttlebutt community, our friends and family who participated in and contributed to this reflective process._
