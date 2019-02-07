# Samsung NEXT Stack Zero Grant

https://samsungnexteurope.typeform.com/to/DtpcWw

1. First, tell us your project's name.

Dark Crystal

2. Give us your high-level pitch and tell us what problem you're trying to solve

Dark Crystal is a secret sharing protocol and prototype application. Dark Crystal takes a novel approach to using Shamir's Secret Sharing algorithm, combining narrative, human relationships and ritual with new peer-to-peer technologies to achieve distributed secret persistence. A living prototype has been built ontop of the Secure Scuttlebutt stack, a peer-to-peer offline-first gossip protocol, database and mesh network.

On Scuttlebutt, records in a locally stored append-only database are gossiped and replicated between peers across a shared network by up to n degrees of separation. This persistence model makes for immense resilience. Once committed and gossiped, all data, private or public, can be recovered from the mesh without its contents being exposed. In addition, this data can never be deleted.

We posit that this persistence model is transformative when applied to the wicked problem of effective and secure key management. In its prototype form, Dark Crystal extends the Scuttlebutt ecosystem, enabling peers to securely back up secrets (private keys, seeds, passwords and other sensitive information) using the trust in their social network.

Your secret is split into 'shards', encrypted with the relevant Ed25519 keys and sent to selected friends. If your identity becomes compromised, you become locked-out, or lose your secret, your peers can recombine the shards to recover it for you. Whenever you need to regain access, you can request the shard from each custodian, only exposing the original secret once the desired quorum is reached and proof of identity is achieved. Dark Crystal makes this process simple, minimising human error and increasing accessibility. It is a resilient system of collective data ownership.

We believe this social model of data custody has many implications and usecases. First and foremost, when distributing sensitive encrypted information, such as a cache of documents, both the documents themselves and the encrypting key can be 'sharded' and distributed to peers within this unregulated mesh network. Th

Distributing sensitive encrypted information, including a cache of files,

It is a critical tool for anyone needing to reliably distribute sensitive information between a small group, anyone at risk of losing their device, and anyone who needs a secure backup for keys or passwords without needing to rely on hardware devices or trusted authorities.

3. Which fields or areas does your technology impact the most? Feel free to use comma-separated tags.

Privacy enhancement, Cryptography, Peer-to-peer web, Distributed applications, Personal data management, Blockchain technology, Security, research, and educational initiatives

4. Do you have a website? A public code repository would do. 

web:
darkcrystal.pw

ssb:
#dark-crystal #darkcrystal and #mmt on Scuttlebutt

Source code
Client plugin / UI: github.com/blockades/patchbay-dark-crystal
API: github.com/blockades/scuttle-dark-crystal
Data schemas: github.com/blockades/ssb-dark-crystal-schema


5. Where is the team based? If distributed, give us a general idea.

- Alanna Irving, NZ
- Dan Hassan, AUS / UK
- Kieran Gibb, UK
- Mix Irving, NZ
- Peg, DE


6. If accepted, how will you utilize the grant?

Our backgrounds and passions are in cooperatives, communities, and high-trust networks. We take the approach that development of new technologies must be rooted in communities, not as an abstract solution applied to a perceived problem. As such we organise and communicate in public on Scuttlebutt. All development has stemmed from a protracted period of research and is completely open source.

### 1. Research and groundwork - Sept 2017 - June 2018

- Discussions within and without the Scuttlebutt community about how to expand which humans get to be a peer in this new p2p sneakernet        

- Hundreds of hours of education sessions, interviews and workshops at a variety of events exploring engaging with crypto, figuring out peopleâ€™s         primary pain points preventing participation

- Experiments with sharing and using crypto-currency wallets in a group, discovering what happens when someone loses a password or becomes         incapacitated

- Private key backups emerged as the wicked problem at the crux of what allows these systems to be accessible


Budget: $130,000 USD - COMPLETED

        
### 2. Dark Crystal v1.0 - July - Aug 2018

- Develop data model schemas and build an API to access the database

- Integrate cryptographic mechanisms and message passing

- Integrate secure encrypted end to end messaging and shard distribution

- Ensure data replication and resilience (no data loss) using gossip protocol (SSB)

- Plugged into Patchbay SSB client

- Release on SSB as reference client and reference ecosystem

Budget: $22,000 USD - COMPLETED

### 3. Dark Crystal v1.5 - 2 months

- Test v1.0 with a varied user base with an emphasise on assessing accessibility

- Integrate feedback to optimize terminology and user flows

- Improve the user interface and community interface

- Port the application into the most popular SSB client (Patchwork)

- With support from visual designers, integrate extensive easy to understand documentation to increase accessibility and facilitate learning about key / secret management practices.

Budget: $60,000

8. Tell us your story: how long have you been working on this project, how is the community involved, or any other detail you want.

The Dark Crystal project started when Dan Hassan gifted 50 people cryptocurrency who otherwise would not have gotten involved in it, and used these experiences as research into what it actually takes to make cryptocurrency accessible to more diverse people. Over the last year, we have zeroed in on safe management of private keys as a foundational problem to solve. Dan Hassan then brought a team together with a track record of delivering new socio-technological open source tools and we got to work.

Members of our team have built the world's first cooperative hedge fund (Robin Hood Coop), created open source software for collaborative organising and financial decision-making (Loomio and Cobudget), grown networks of next-paradigm social impact startups (Enspiral), participated in a 30 year long federation of cooperatives which has never had a default on a loan (Radical Routes), attracted EU funding for investigations into social currency design and community driven decision making (D-CENT and DECODE), and helped create one of the most vibrant growing ecosystems in cipherspace (Secure Scuttlebutt).

Dan Hassan has an MSc in Advanced Computing Technologies, having built a metadata search engine for the Bitcoin blockchain. Mix is a core developer of Scuttlebutt a decentralised p2p cryptographic protocol used for a range of apps from social networking to git. Alanna has co-founded a number of startups specifically in the area of open source tools for financial collaboration, and is an expert in non-hierarchical business structures. Kieran and Peg are accomplished computer programmers and community builders.

We are all experienced in effective collaboration and know how to work as a team. We are a high-EQ group, emphasising the human elements of what it takes to make great software, backed up by technical expertise.


9. What is the most groundbreaking thing about your solution?

Dark Crystal has a working prototype currently being trialled by members of the Scuttlebutt community. It is a supportive and friendly international social network reminissent of early internet forums before spam and distrust became a problem. It is diffucult to reliably estimate the number of scuttlebutt users, but a recent study revealed a minimum of 7000 people on the network. Meanwhile itâ€™s base grows every day.

While we want to build dark crystal as something which can be used by anybody independent of having involvement in this community, we think it is important that it exists as a support network.

We realize there is still much work to be done to expand this community so that people living under oppressive governments are better represented. Our approach is to work towards making the on-boarding process as simple as possible, to minimise language and culture barriers and to focus on accessibility.

If we can overcome these issues, the very mechanism by which our tool works, that each secret holder invites their trusted friends to hold shards, will cause a propagation of the user base in different directions and the community will grow.

10. How does your solution further decentralization?

We believe it is possible and important to expand who gets to participate as a peer in peer to peer systems. Building responsible and consentful interfaces is an integral part of our mission.

11. Where can we find you online (social media, Gitlab, Github, etc.)?


12. Do you agree to our terms and conditions?
    - https://samsungnext.com/wp-content/uploads/2018/10/stackzero-grant-2018-terms.pdf
