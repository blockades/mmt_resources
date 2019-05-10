# Dark Crystal Ethereum Foundation IV Wave Grant Report

![](https://i.imgur.com/Q0GaP8Y.jpg)

> _image caption: a water color which mix drew in the style of three paneled comic about people regathering their crystal shards, then in the middle panel they come back together and in the last panel a golden key is shining magically put back together_
> 

## Summary

In October 2018, the Dark Crystal team were awarded $50,000 to be distributed over a 6 month period by the Ethereum Foundation in the form of a grant to help progress their prototype Scuttlebutt software. This document specifies the deliverables the Dark Crystal team pitched to the Ethererum Foundation and contains a summary and evaluation of the teams progress for each deliverable.

The **Executive Summary** is that all milestones have been accomplished. There has been clarification of avenues for further funding and development which would futher the mutual decentralised aims of both Scuttlebutt and Ethereum (and the wider dweb). This is expanded in Section 12 "Ongoing Discussions and Ethererum Collaborations".


*_Please note all cipher links are viewable within scuttlebutt_*

### Milestone Agreements

**Cipher links:**
_Milestone Agreeements_
%mof4xfyQRJ0rmeEaXp4VA+mcVNy0rc5q7CbAzN9ifvQ=.sha256

3 month milestone  | .
---|:---:
Working beta release, embedded into Patchbay (includes 'forwarding' shares to recover from lost device, and security enhacements) | :white_check_mark: 
Standalone client (proof of concept)| :white_check_mark: 
secp256k1 research document (outlining stategy and challenges for adopting  keys of this form on SSB) | :white_check_mark: 

6 month milestone | .
---|:---:
User testing of our 3 month milestone with a writeup outlining bugs and challenges for less technical users | :white_check_mark: 
Standalone client (full release) | :white_check_mark: 
secp256k1 based `ssb-server` (proof of concept. this is the underlying API which all Scuttlebutt applications communicate with. By proof-of-concept we mean it will pass tests, but not yet be in use 'in the wild'. | :white_check_mark: 
Collaboration with an Ethereum team | :clock1030:

:clock1030: = we've had calls with Meta Mask, but haven't formulated a clear plan (yet) about what the best collaboration could be (key backup, or ssb in metamask)


#### Outside of formal milestone agreements but things we think are good idea:

- Continue communicating research through ethresear.ch
- Continue networking within the Ethereum ecosystem, looking at existing key recovery strategies and taking steps towards collaboration.
- Mentioning Ethereum in our publicity materials (eg: making the secret treasure map be ETH seeds etc).

## Achievements (Shipped)

The 3/6 month milestones were quite broad, and we managed to exceed them, explore further terrain and deliver a lot more. Here's a non-exhaustive overview of all of the things delivered (includes further detail on the milestones as well):



1. Upgradeable shard encoding, ensuring backwards compatability

2. Forwardable shares, allowing recovery of secrets in the case of stolen or lost devices.

3. Better secret encoding, adding validation capabilities and better compression.

4. Ephemeral shares, meaning keys secrets can and their shares can be forgotten / "deleted"

5. 'Nicknames' as secret metadata

6. Local discovery of peers for replication

7. A standalone client

8. Usability Assessment through peer review and design residency

9. Improved UI designs and onboarding

10. secp256k1 research for Scuttlebutt

11. Conferences and Residencies : DevCon4 in Prague, Agorama in London, the UnderExposed Residency in Berlin, and Rebooting the Web of Trust, Barcelona.

12. Ethereum Community collaborations - discussions with members about key recovery strategies and future collaborations

13. Faster Initial Sync

### 1. Upgradeable shard encoding

In our initial prototype process, we anticipated we would be likely be making breaking changes to our data schemas and added a basic version string as an attachment to our messages. In November as we began researching the challenges of implementing forwarding shares and making secrets validatable, we quickly discovered that in order to make any significant changes to our codebase and still be able to accomodate existing records in Scuttlebutt's append-only log, we would need to mark this as a high priority item. Our initial development phase was primarily concerned with ensuring a correctly functioning schema validation system based on semantic versioning.

This was an early success and opened the door to continued and iteratable development. It should prove to be an excellent resource for the scuttlebutt community and anyone wishing to develop other applications on this stack.

**Web links**:
https://github.com/ssbc/ssb-schema-validation

**Cipher links**:
_Schema Versioning_
%q as secret metadata

6. Local discovery of peers for replication

7. A standalone client

8. Usability Assessment through peer review and design residency

9. Improved UI designs and onboarding

10. secp256k1 research for Scuttlebutt

11. Conferences and Residencies : DevCon4 in Prague, Agorama in London, the UnderExposed Residency in Berlin, and Rebooting the Web of Trust, Barcelona.

12. Ethereum Community collaborations - discussions with members about key recovery strategies and future collaborations

13. Faster Initial Sync

### 1. Upgradeable shard encoding

In our initial prototype process, we anticipated we would be likely be making breaking changes to our data schemas and added a basic version string as an attachment to our messages. In November as we began researching the challenges of implementing forwarding shares and making secrets validatable, we quickly discovered that in order to make any significant changes to our codebase and still be able to accomodate existing records in Scuttlebutt's append-only log, we would need to mark this as a high priority item. Our initial development phase was primarily concerned with ensuring a correctly functioning schema validation system based on semantic versioning.

This was an early success and opened the door to continued and iteratable development. It should prove to be an excellent resource for the scuttlebutt community and anyone wishing to develop other applications on this stack.

**Web links**:
https://github.com/ssbc/ssb-schema-validation

**Cipher links**:
_Schema Versioning_
%q as secret metadata

6. Local discovery of peers for replication

7. A standalone client

8. Usability Assessment through peer review and design residency

9. Improved UI designs and onboarding

10. secp256k1 research for Scuttlebutt

11. Conferences and Residencies : DevCon4 in Prague, Agorama in London, the UnderExposed Residency in Berlin, and Rebooting the Web of Trust, Barcelona.

12. Ethereum Community collaborations - discussions with members about key recovery strategies and future collaborations

13. Faster Initial Sync

### 1. Upgradeable shard encoding

In our initial prototype process, we anticipated we would be likely be making breaking changes to our data schemas and added a basic version string as an attachment to our messages. In November as we began researching the challenges of implementing forwarding shares and making secrets validatable, we quickly discovered that in order to make any significant changes to our codebase and still be able to accomodate existing records in Scuttlebutt's append-only log, we would need to mark this as a high priority item. Our initial development phase was primarily concerned with ensuring a correctly functioning schema validation system based on semantic versioning.

This was an early success and opened the door to continued and iteratable development. It should prove to be an excellent resource for the scuttlebutt community and anyone wishing to develop other applications on this stack.

**Web links**:
https://github.com/ssbc/ssb-schema-validation

**Cipher links**:
_Schema Versioning_
%qwrdable shares

The team spent several weeks calculating and weighing up the social component and technical challenges faced when dealing with the forwarding of shares and what this would mean for the existing API. This began with a series of role-play exercises simulating an SSB user sharding their private key using the software, losing their account and attempting to recover this from their peers. In November, after negotiating the moving parts and developing a semantic versioning system (see [#1](#1)), the team developed a new set of schemas for forward-type messages and functions for publishing to the SSB log and pulling these records as a data stream. By December, the team were integrating these into the existing front-end module `patchbay-dark-crystal` and opened up this raw functionality to users in a soft release by Christmas. The schemas and API were comprehensively tested in Tape.

**Web links**:
https://github.com/blockades/ssb-dark-crystal-schema/blob/master/schemas/forward/v1.js
https://github.com/blockades/scuttle-dark-crystal/tree/master/forward
https://github.com/blockades/patchbay-dark-crystal/pull/19

**Cipher links**:
_Coconut Death Scenarios_
%W5tFGtKQwXQzyXwqIc54nuK9T0zDqlFQjE0YpS9bAq8=.sha256

_Brainstorming coconut-related scenarios_
%yAdCqJqI+ihjhCt6DGX9YBhtxujM9P9bwRAjVIZZvKo=.sha256

_Interface for 'forwarding shards' / ssb identity recovery for dark crystal_
%jjwraPO8OqwAwb8aBw4wjjyZtZv3YRXnHTAgwwVdvec=.sha256

_Choose your own adventure UI Wireframing_
%nnkcHzSx2Cr6UHFxWfYjKg2n/oH864G269EAIe9fTfw=.sha256

![](https://kyphae.keybase.pub/dark-crystal/screenshots/standalone-v0/dark-crystal_forward-create.png)

![](https://kyphae.keybase.pub/dark-crystal/screenshots/standalone-v0/dark-crystal_forwards.png)

![](https://kyphae.keybase.pub/dark-crystal/screenshots/standalone-v0/dark-crystal_forwarded-crystals.png)

### 3. Better Secret encoding

The team considered the possibility that genuine holders of shares might have a motivation for not wanting the secret to be recovered, and could maliciously modify their share. Furthermore, the shares might be modified by some accidental or external cause, and it is important to be able to determine which share is causing the problem.

In order to verify a secret is 'as it should be' once recovered, an identifier is added to the share to allow the correct secret to be automatically recognised. When we create a set of shares, we create a MAC (we perform a SHA256 of the secret and slice off the last 32 characters), and concatenate that with the secret. When the shares are reconstructed into a secret, at the moment, if you provide an invalid share, instead of receiving the actual secret, the algorithm returns a 'garbage' string. We can validate this by recreating a new MAC using the recovered secret and checking to see if the new MAC matches the MAC contained within the recovered secret. If the MAC doesn't match, we can assume that one or more of the shares have been tampered with. If it does match, then we know that we have a set of valid shares for the secret that was reassembled, and therefore we have an actual secret.

These changes were bundled initially into the `secrets-wrapper` in a PR to `scuttle-dark-crystal` and eventually exctracted as a separate npm package called `dark-crystal-secrets`.

Further development needs to be done in order to validate shards individually, thus screening out malformed or maliciously sent dud shares.

**Web links**:
https://ethresear.ch/t/security-considerations-for-shamirs-secret-sharing/4294
https://github.com/blockades/dark-crystal-secrets
https://github.com/blockades/scuttle-dark-crystal/pull/25

**Cipher links**:
_Security review of Dark Crystal by Dominic Tarr_
%XVS1gYKaq2LCpcjjmW7VT5AT6NLQ8CBuEgwQphGiI1M=.sha256

### 4. Ephemeral Shares

Following a security review and comments on our approach from some of the Scuttlebutt community's most experienced cryptographers, it became apparent that ephemeral messages would be highly useful in many respects, particularly for enabling the deletion of a recovered secret.

The team integrated these solutions, working together with one of SSB's core cryptographers to implement a plugin for ephemeral messages. In addition a pull-request is in the process of being reviewed that implements ephemeral shard return. On requesting the return of a shard from a custodian, the secret holder generates an ephemeral key for each custodian and sends this with the request, them to encrypt the share with the sent key before sending the share back. On receiving all the keys and revealing the secret, the secret holder can now delete the private keys that were used to encrypt each share. Thus effectively deleting the shares and thus the secret from their log.

Ephemeral keys are a significant feature addition for the application, and open up the possibility of revoking trust, a feature we as a team are excited about.

**Web Links**:
https://github.com/ssbc/ssb-ephemeral-keys
https://github.com/blockades/scuttle-dark-crystal/pull/44

**Cipher links**:
_Revoking trust - deleting shares_
%eYqUfFjpI7Lcru8CLEHxTuML/nbNUz/BL9R72P6CYHc=.sha256

_Forward Secrecy of shards_
%L/GV/qWmD/TrucTw/P1UNy6+SpkPqaENNT7lPR4HJo4=.sha256

_Ephemeral Shares Discussion_
%hNnHqpww6Imi+cbauGK4dkn3Wpfrb8G+Ab5g/5j6dCQ=.sha256

### 5. Nickname Metadata

Due to loss of context after forwarding shards, some kind of description of a recovered secret was seen as required in order to assist the user in remembering what it was for (in the case of a private key, this could be one of many that all look very much the same). This feature added a label or nickname to the secret that was passed _as part of the secret itself_ to ease the loss of context.

When we come to look at the inheritance case, this feature is going to be highly useful. Pamela Morgan repeatedly makes clear in her book 'Crypto Asset Inheritance Planning' that giving hiers access to keys is only half of the story. They need to know what to do with them.

**Cipher link**:
_Adding 'Nicknames' to secrets in dark-crystal_
%B0un39A24N10E1BprJeHhFRp/MMbbNI6q0Pn81yxPnI=.sha256

### 6. Local Peer discovery

A long sought-after feature, Patchbay and Dark Crystal now gives indication about connected peers _in app_, in addition to providing information about your gossip rate and showing an indicator that new data is arriving / being indexed.

**Cipher links**:
_Local Peers_
%UFNyDPheJBSIWiuLvbmv3qM3y1vzofAHmQsH/b7Ew/Q=.sha256

### 7. Standalone Client

By January, the team built a standalone Electron application which works on multiple platforms (MacOS, Linux, Windows). This is a stripped back version of Patchbay (which provided many of the  dependencies required by the front-end framework `patchbay-dark-crystal`). Further development on the interface was delayed until significant peer review and a usability assessment could be carried out.

Following a significant phase of peer testing and review and UI design iteration, the team began making changes to the standalone application. Development work in this area is ongoing. We currently have a functional client that retains most of the functionality added through the last 6 months of development. We have yet to test its ability bundle as an installer and whether it works multiple platforms. We anticipate this will be fully functional by the end of March and (following the soft release of shard forwarding at Christmas) are planning a hard release of Dark Crystal as a standalone client by early May.

**Web links**:
https://github.com/blockades/dark-crystal-standalone

**Screenshots**:
_January standalone client_
https://keybase.pub/kyphae/dark-crystal/screenshots/standalone-v0/

_Following UI redesign_ ([`see development branch`](https://github.com/blockades/dark-crystal-standalone/tree/development))
https://keybase.pub/kyphae/dark-crystal/screenshots/standalone-v1/

![](https://kyphae.keybase.pub/dark-crystal/screenshots/standalone-v1/dark-crystal-standalone_secrets-index-1.png)


### 8. Peer Review and Usability Assessment

Peer testing was undertaken by members of the Dark Crystal team through individual and group sessions at multiple meetups and events across a period of two months. Much of the feedback opinions and data was collected at the Simply Secure design residency in Berlin in January 2019, at Agorama Sever Coop in London in February 2019 and at Art Hack in Wellington, NZ in January 2019.

Dark Crystal's strengths currently lie in a very clear conceptualisation of the process of sharing secrets among trusted peers. Once peers had explored the application and gained a knowledge of the context in which to apply make use of it, the nuance of this analogy was widely appreciated and most people interacted fairly intuitively with the application. Overall we received a lot of excitement about the project and its stated goals, and there was significant enthusiasm about the implementation so far.

Our review exposed significant UX challenges and indicated our suspicions that a protracted phase of UI development was required. 

**Web links**:
https://github.com/blockades/mmt_resources/blob/master/research/dark_crystal-report_peer_testing_and_usability_assessment.md

**Cipher links**:
_UnderExposed Residency Design Workshop with Ura Design: Part One_
%QqKBQTL0hoslzjFMWwBInwO660RFvb41PKI/taqa22E=.sha256

_UnderExposed Residency Design Workshop with Ura Design: Part Two_
%qtEIi+IfbwN0s9fM8SfLNp4eW8VuTnp7mDzwS84JBr0=.sha256

### 9. UI Designs and Onboarding

Beginning in November, team members pitched simple wireframes for their view on what the UI could / should look like, particularly in regard to newly added functionality (shard forwarding). This served as an initial tool to easily create a simple UI that we ancitipated would require significant changes in the future following our peer review phase (see [#8](#8)).

Following the usability assessment in January and February, team members drew on the set of challenges raised to pitch new wireframes. These are being integrated directly into the ongoing development in the standalone client (see [#7](#7)).

One team member significantly improved the mentioning system native to scuttlebutt, to more easily enable finding and selecting custodians for your shares.

A core challenge of the usability review was the ongoing onboarding challenge Scuttlebutt has. This includes the ease by which people can connect to the network and unresponsive interfaces during replication and indexing. One member of the team is in the process of designing and building a simple onboarding application that acts as a wrapper for other Scuttlebutt applications, easing the experience for first-time users.

**Web links**:
https://github.com/ssbc/ssb-ahoy
https://github.com/ssbc/patchbay/pull/316

**Cipher links**:
_Wireframes_
%jjwraPO8OqwAwb8aBw4wjjyZtZv3YRXnHTAgwwVdvec=.sha256
%7xQFL3WKruIiNa/nBiPuPx9rGw+FA6iGnzid9t1AqFM=.sha256
%ceQJEYpX3ngT+pmXFZB5Lmwjd4jBdNGLTxi44oLLTQM=.sha256

_Early standalone client UI_
%9MbF6oN3Z2I94I8x6/jl8fASK0JRSkVVt+FDtikospw=.sha256

_ssb-ahoy for easy onboarding_
%QS86lcEfQbGXEqu25EGZc2MegxJvDGpJCvPuAAT/KuY=.sha256
%KFnMyQ8De+NGQigxt4imP62PlEoGqYtJMbHhWRN+tMA=.sha256
%rfR4VYjo5ZCsycdK/w4qNwi9iwBDdNQ1ULzT2J4MX24=.sha256

**Cipher blobs**:
&ERGA0oJCELz2s4sr47f75iXZComB/2akzZq+IpcuqDs=.sha256

![](https://kyphae.keybase.pub/dark-crystal/screenshots/standalone-v1/dark-crystal-standalone_secrets-new-trust.png)

### 10. Research on using secp256k1 keys

As a proof of concept, we implemented secp25k1 signing keys and feedIds on Secure Scuttlebutt and published messages signed with these keys to a test network.  We also produced a report documenting the advantages of the SSB protocol in the context of off-chain transport for Dapps, possible issues with our model, and possible alternative approaches. This document went viral through Ethereum reddit and twitter for a couple of weeks after release which we found interesting and an additional sign that there is interest of such integrations with the wider Ethereum ecosystem.

**Web links**:

_Report on interoperability between the Ethereum and Secure Scuttlebutt networks_
https://github.com/blockades/mmt_resources/blob/master/research/secp_writeup.md
_Feasibility study of implementing secp256k1 on Secure Scuttlebutt_
https://ethresear.ch/t/implementing-secp256k1-on-secure-scuttlebutt-ssb-to-create-cross-platform-ethereum-scuttlebutt-applications/4848

_Proof of concept for secp256k1 key generation, signing and validation_
https://github.com/blockades/ssb-keys
https://github.com/blockades/ssb-ref

**Cipher links**:
_Ongoing discussion on this over the last 5 months_
%6xDjaCQ1DIDvhIxqulZ6JsvxDp2LkYX/tvGWv1HL68g=.sha256


### 11. Conferences and Residencies

The team was able to attend many conferences, run presentations and workshops exploring the solutions generated and problems posed by social secret sharing as a pattern within the p2p technology world and beyond.

**Cipher links**:
_Lightning talk at DevCon4, Prague_
%IElYErpencvUW+e8uYUFayAQORk3uG888Rp097W3CDY=.sha256
%MoElms3qM5p0Lkq9x47nKsPA7GPPMooc38Nja/a1SoY=.sha256


_'Underexposed Design Residency' workshop with ura.design, Berlin_
%QqKBQTL0hoslzjFMWwBInwO660RFvb41PKI/taqa22E=.sha256
%qtEIi+IfbwN0s9fM8SfLNp4eW8VuTnp7mDzwS84JBr0=.sha256

_'Rebooting the Web of Trust 8', Barcelona_
%IC6IUtNhMqdKWySd1/r2bzmey9xnxBgXNya7UrySkXw=.sha256

**Web links**:

_Lightning talk at #devcon4 about http://darkcrystal.pw built within #scuttlebutt  :seedling:_
https://slideslive.com/38911795/dark-crystal-secure-scuttlebutt

_'An introduction to Scuttlebutt' at Space4, London_
https://tenthousandthings.org.uk/community-sovereignty-scuttlebutt/

_'Offgrid Connections: from Earth to Mars' at MozFest 2018, London_ 
https://tenthousandthings.org.uk/offgrid-connections/

_Our draft paper on social recovery written at 'Rebooting the web of trust', Barcelona_
https://github.com/WebOfTrustInfo/rwot8-barcelona/blob/master/draft-documents/Evaluating-social-recovery.md

### 12. Ongoing Discussions and Ethererum Collaborations (and possible fundable future(s))

The main discussions we have been having over the last 6 months have been as follows:

1. Scaling of dweb in general; Wendell
2. Adding cross compatibility of Ethereum (and other blockchain projects) curves (secp256k1) into SSB; Wanderer
3. Collaborations with Ethereum projects; MetaMask, Parity Technologies and MakerDAO (and some others involved in DappHub)
4. Further funding collaborations through Gitcoin

**(1) Scaling of dweb in general**
We have been speaking with people in the ecosystem, such as Wendell, about envisioning scaling as an ecosystem wide concern. With this lense we have been viewing what place SSB has in being a drop in replacement for Whisper. SSB has reached where it has gotten to on a shoestring so we have been discussing what would be needed in terms of mid term stability to acheive maturation of SSB as a commons utility part of a wider suite of technologies supporting decentralisation. $50k USD would pay for a developers main focus in the SSB ecosystem. We have about 20 or so developers which would fit this bill. If we could get a 2 year runway for that number of developers magic would happen.

**(2) Adding cross compatibility of Ethereum (and other blockchain projects) curves (secp256k1) into SSB; Wanderer**

See secp256k1 report. We also have the following suggestion from wanderer:

**Cipher links:**
%e5dRAjMRHtnQ8GMjz5hQkgUeNOfG0+aOL2HCp+VngAE=.sha256

>> peg: i'd love to hear your opinions, particularly on the general question of what could this actually allow people to do that they couldn't do by just publishing a signed ssb message with their ethereum address (or their ssb id to the blockchain). because the thing im finding hardest about this is not having a well defined problem we are trying to solve.

> wanderer: yeah this is hard for ethereum in general since its so generalized it doesn't have a well defined usecase. Ethereum was original suppose to be a triad of protocols, the blockchain for things that need global consensus, swarm for persistent storage and whisper for ephemeral messaging. Ethereum on a whole is suppose to be a "global computer" and like any computer it will need dedicated subsystems for dealing with certain critical tasks. I think SSB could be usefully in this view for several things.

> Programs or "dapps" could use ssb for persistent storage, much of how it is used for things like ssb-chess, but combined with ethereum could open other possibilities, such as controlling assets with the state of a chess game ("ex the winner of this chess tournament get a shiny cryptokitty!"). Why use ssb over swarm? swarm also suffers form slow update times much like ipfs's ipns and it has never really gained any traction.
1.a) to do this, ethereum could be represented as a feed inside scuttlebutt, instead of just using scuttlebutt to bootstrap the network, it might be possible to use scuttlebut directly. This would be more way more complicated but lets pretend for a second that we have a way to have flexible feed definitions. Where a feed is some ordered sequence of messages and a validation function for that set of messages. Its easy to see that blockchian is an ordered set of messages, each block points back to the last block and there is only one sequence of block. The validation function for a blockchain would be more complicated then scuttlebutts, but lets say there is some way to optional load a "plugin" to do the validation if the user wants that functionality. This would allow scuttlebut apps to read directly from the blockchain.

> 1.b) building on 1.a, sec256k1 tx feeds could also be added in the same way. In ethereum a tx consists of a nonce, signature, data... ect, but doesn't included the previous hash of the last tx, but this is not a problem as that could just be appended to the data section of the signature. ethereum tx feeds would allow scuttleapps to read and write to ethereum

> 1.c) Ethereum has a JS API, if scuttlebutt had something that was equivalent, ie, a somewhat stable API for apps to uses instead of adhoc API that is different between clients, then It would ("should/handwavey") be easy for ethereum dapps to simple included "scuttle.js" and start reading and writing to scuttlebut, much the same way dapps use ipfs today.

> Network security. Ethereum uses a DHT to find peers. This has the problem that a given node could be a target for an eclipse attack. Using scuttlebutts' trustgraph to bootstrap networking for ethereum could provide security against this type of attack. It could also incentize miners to act as pubs (if we a proper fee market for tx's then miners would want to connect to many clients to get as many tx's as possible)...
lastly going along with 2) scuttlebut could be used bootstrap a state channel network or a plasma network. This would actually be the optimal way to build things like a chess tournament.
so to recap, we don't still don't have a single well defined problem we are trying to solve on the app level. But maybe a good thing to think about solving is a chess tournament. On the protocol level there are 2 problems we could solve 1) network bootstrapping and 2) being a db for dapps

**(3) Collaborations with Ethereum projects; MetaMask, Parity Technologies and MakerDAO (and some others involved in DappHub)**

We are in the process of mapping out a collaboration with MetaMask to incorporate SSB and Dark Crystal into MetaMask. This would be a high leverage project as it would open the Dark Crystal pattern to ~ million new users. The fusion with SSB would provide MetaMask with some needed replication functionality which they are needing for their mobile client, usability and general backup capabilities. There are a high number of people on the MetaMask (both designers and coders) team excited by this and willing to gift their time to the fusion. There is more work to be done in figuring out the specification and minimal shippable features.

**Web links**:
_SSB in MetaMask Anchor Issue_
https://github.com/MetaMask/metamask-extension/issues/6318
_Enable sharding of seed in MetaMask_
https://github.com/MetaMask/metamask-extension/issues/1292
_Social Recovery using Dark Crystal in MetaMask_
https://github.com/MetaMask/metamask-extension/issues/6308


**Cipher links**:
_Discussion with Frankie B about Metamask collaboration_
%p2zJ7HnBaEC+ZA4NGdSUbLWIyEn1EJyYNZ4euOESKqM=.sha256

_Discussion on minbot proof of concept for a ssb-server which could run in the browser_
%pWD2sG3mNY4JatvIjr030gbbOU5OryrwdER9PZRoKEc=.sha256

**(4) Further funding collaborations through Gitcoin**

Since receiving the Ethereum Foundation IV grant we have been collaborating with Gitcoin to match fund new requested features for Dark Crystal and also SSB.

We have collaborated on:

Important bugfix in Patchwork
https://gitcoin.co/issue/ssbc/patchwork/877/1712

Dark Crystal CLI
https://gitcoin.co/issue/blockades/scuttle-dark-crystal/24/1688

Ephemeral Shard Returns
https://gitcoin.co/issue/blockades/scuttle-dark-crystal/47/2164

Dark-Crystal-Secrets HTTP API
https://gitcoin.co/issue/blockades/scuttle-dark-crystal/45/2151

Dark Crystal Patchwork Integration
Phase 1 - https://github.com/ssbc/patchwork/issues/952
Phase 2 - https://github.com/ssbc/patchwork/issues/953
Phase 3 - https://github.com/ssbc/patchwork/issues/954

We have also been on the Gitcoin Community screencast (27 mins in)

https://github.com/gitcoinco/community
https://consensys.zoom.us/recording/play/XSyggFA--Zb3MSrjXnMwu33q07IDdxbamW9bBTEgPx6f8IaWh1Dtm4xsGncOLQdv?autoplay=true&startTime=1543615411000


### 13. Faster Initial Sync

![](https://i.imgur.com/2nHh6wI.jpg)

One of the most difficult things about getting new people set up with Scuttlebutt, is the "initial sync". It involves moving about 300-600MB of your friend (and their friends) messages, and then indexing them.

Current Client all try to do this whil displaying you the data, which makes for a terribly choppy and confusing experience.

We've made a new tool called `ssb-ahoy` which any client in Scuttlebutt can use and takes care of this Initial Sync gracefully, while providing some basic info about scuttlebutt, and some visuals to help people understand what's going on.

npmjs.com/ssb-ahoy

