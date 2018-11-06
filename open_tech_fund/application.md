# Open Technology Fund

## What is your project name? 
Dark Crystal

## What is your idea?
*Describe it - Content limited to 2000 characters*
       
Dark Crystal is a secret sharing protocol and prototype application. Dark Crystal takes a novel approach to using Shamir's Secret Sharing algorithm, combining narrative, human relationships and ritual with new peer-to-peer technologies to achieve distributed secret persistence. A living prototype has been built ontop of the Secure Scuttlebutt stack, a peer-to-peer offline-first gossip protocol, database and mesh network.

On Scuttlebutt, records in a locally stored append-only database are gossiped and replicated between peers across a shared network by up to n degrees of separation. This persistence model makes for immense resilience. Once committed and gossiped, all data, private or public, can be recovered from the mesh without its contents being exposed. In addition, this data can never be deleted.

We posit that this persistence model is transformative when applied to the wicked problem of effective and secure key management. In its prototype form, Dark Crystal extends the Scuttlebutt ecosystem, enabling peers to securely back up secrets (private keys, seeds, passwords and other sensitive information) using the trust in their social network.

Your secret is split into 'shards', encrypted with the relevant Ed25519 keys and sent to selected friends. If your identity becomes compromised, you become locked-out, or lose your secret, your peers can recombine the shards to recover it for you. Whenever you need to regain access, you can request the shard from each custodian, only exposing the original secret once the desired quorum is reached and proof of identity is achieved. Dark Crystal makes this process simple, minimising human error and increasing accessibility. It is a resilient system of collective data ownership.

We believe this social model of data custody has many implications and usecases. First and foremost, when distributing sensitive encrypted information, such as a cache of documents, both the documents themselves and the encrypting key can be 'sharded' and distributed to peers within this unregulated mesh network. Th

 Distributing sensitive encrypted information, including a cache of files,

 It is a critical tool for anyone needing to reliably distribute sensitive information between a small group, anyone at risk of losing their device, and anyone who needs a secure backup for keys or passwords without needing to rely on hardware devices or trusted authorities.


Character Count: 1983

---

What are hoped for goals or longer term effects of the project?

---
- The difficulties of private key custody are an ever increasing problem in the areas of encryption, digital identity, and cryptocurrency.  We want to solve these problems using the power of **friendship networks** and **human trust**. 

- We hope that solving these problems will **make encryption tools more accessible**, and that journalists or activists using such tools will not be hindered by loosing their computer, becoming incapacitated or being captured.

- We want to provide a solution whereby the custody of a sensitive document or piece of information can be distributed between a group in such a way that the group must **agree together** if and when it is safe to publish it. 

- We want to create a storage solution for sensitive documents which would allow the owner of those documents to cross international borders without having the documents on their person, nor relying on any company, authority or piece of hardware, and are able to recover the documents at will when the time is right.

- We want to make a system of sharing custody of secrets which works independently of any third party or authority, and even of having an internet connection. This has big implications for people living in regions with **poor connectivity** or **net neutrality** issues.

- We hope that by powering such tools by trust and friendship, we can alter the topology of our individualist and competitive society, and bring a sense of community and cooperation.
---
Content limited to 2000 characters - We want to know how you think the world could be, what larger purpose this project is a part of, and/or the bigger target you aiming for. Bulleted lists are good.


---

## Focus *
- [x] Access to the Internet 
- [ ] Awareness of access 
- [x] Privacy enhancement 
- [ ] Security from danger or threat online

---

## Status *
- [ ] Just an Idea (Pre-alpha) 
- [x] It Exists! (Alpha/Beta) 
- [ ] It's basically done. (Release) 
- [x] People Use It. (Production) 

---


## Technology attributes *
If the proposed project is working very closely with technology such as developing software or hardware, select any of the following that could describe the technology.

- [x] Browser extension 
- [x] Browser plugin 
- [ ] Unmanaged language 
- [x] User interface/experience 
- [ ] Anonymity 
- [x] Application deployment 
- [ ] Web application 
- [ ] Server daemon 
- [ ] Web API/Mobile application (serverside) 
- [x] Mobile application (clientside) 
- [x] Cryptography 
- [x] Desktop client 
- [x] Desktop App 
- [ ] Dependency integration 
- [ ] Software as a Service (SaaS) 
- [ ] Platform as a service (PaaS) 
- [ ] Infrastructure as a service (IaaS) 
- [x] Sensitive data 
- [x] Networking 
- [x] Wireless Communication 
- [ ] Hardware/Embedded device(s) 
- [ ] Reverse Engineering 
- [ ] Other 
- [ ] Not applicable 

---

## How will you do it?
Describe how. Briefly and clearly list key milestones, objectives, and/or activities briefly. These should be specific, measurable, attainable, realistic, and time-relatable. Bulleted lists are ideal.

---
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

### 4. Dark Crystal v2.0 - 6 months

- Build a standalone client application that functions independently of other SSB clients

- Enable your peers to recover your secret without your involvement, in the case of incapacitation, death, or your identity is lost / compromised

- Acquiring consent for custody of a shard

- Storing and recovering large secrets; file encryption        

- Enable broader access by integrating i18n (internationalization)

- Attach instructions to a secret shard to provide more information to custodians

- Explore the possibility of mobile implementation to improve access

Budget: $150,000

### 5. Research and maintenance - 4 months

- Pursue research and education projects with allied groups in Greece, Spain / Morocco and other gateways to the fortress. 

- Integrate results of trials with stateless groups including refugees and at-risk populations. Implement support for specific use cases for these contexts.

- Integrate research and feedback into application.

- Write a white paper compiling research, protocol and its application.

- Port into MMMMM, a prototype Android SSB client.

- Investigate portability of the protocol into other p2p ecosystems (Holochain, Ethereum DAO, etc)

Budget: $90,000


---

## Objective(s) *
Choose the options that most applies to the proposed effort.

- [x] Research 
- [x] Technology development 
- [x] -Deploying technology 
- [x] -Software or hardware development 
- [x] -Testing 
- [ ] Training 

---

## How long will it take? *
12 months

---

## How much do you want?
$300,000

---

## Who is the project for?
Content limited to 2000 characters. Describe them - In other words, who are the people benefiting or affected most by this effort and how well do you know them?
                                      

* **Anyone using encryption** will benefit greatly from improved key integrity.  We plan to implement features to integrate with GPG for handling private keys and revocation certificates.

* Anyone with a lifestyle which means they are at risk of losing a computer or device, or **do not have a secure place to store things**.  Such as refugees, homeless or vulnerably housed people.

* Anyone living in an oppressive regime who is in custody of sensitive information and concerned for their **privacy**. A journalist or activist who has authored some 'whistleblowing' documents might want to give keys or passwords to a friend in case they get captured.  But this could actually endanger that friend.   Our tool solves this problem by distributing the responsibility, and meaning that a small group must collectively decide if and when it is safe to publish the documents.

* Anyone with **poor or no internet connectivity**.  This is an offline-first peer to peer application which can function independently of the internet.  Furthermore, the gossip protocol allows the spread of information between peers with internet connectivity and those without, as well by syncing devices which move between physical locations.

* Refugees are often unable to carry particular documents with them as they have to cross international borders where it might be unsafe to carry such information.  However they might need particular information for evidence for an asylum claim later. In such a case, the integrity of encryption keys or passwords might have paramount importance and this is an issue which our project addresses. 

* We think the notion of **trust within a small community** of people is a concept that is well understood and endorsed by people from a **wide variety of cultures**.  

We believe Dark Crystal is not just an application, but a protocol that blends a specific set of human / machine behaviours,combining secure key management with socially distributed responsibility. As such it is a protocol that is replicable across different distributed systems and has the potential to reach a broad base of beneficiaries. In other words, its got legs.

---

Content limited to 2000 characters. 

## What community currently exists around this project?

Define the community as you see it. If your answer is none, please explain how you plan to cultivate community around the proposed effort, including mechanisms to receive feedback and get others involved.

---

Dark Crystal has a working prototype currently being trialled by members of the Scuttlebutt community. It is a supportive and friendly international social network reminissent of early internet forums before spam and distrust became a problem. It is diffucult to reliably estimate the number of scuttlebutt users, but a recent study revealed a minimum of 7000 people on the network. Meanwhile itâ€™s base grows every day. 

While we want to build dark crystal as something which can be used by anybody independent of having involvement in this community, we think it is important that it exists as a support network.

We realize there is still much work to be done to expand this community so that people living under oppressive governments are better represented. Our approach is to work towards making the on-boarding process as simple as possible, to minimise language and culture barriers and to focus on accessibility.  

If we can overcome these issues, the very mechanism by which our tool works, that each secret holder invites their trusted friends to hold shards, will cause a propagation of the user base in different directions and the community will grow. 

(this section needs expanding, something about building a trust network, how will vulnerable people find out about this, building community in areas with oppressive governments...not sure whether to mention our links with migrant support group/the social centre in athens)

---

Beneficiaries *
- [x] General public 
- [ ] Women 
- [ ] Youth 
- [ ] Sexual minorities 
- [ ] Ethnic minorities 
- [x] Activists 
- [x] Journalists 
- [ ] Advocacy groups/NGOs 
- [ ] Academia 
- [ ] Technologists 
- [ ] Entrepreneurs 
- [ ] Government 
- [ ] Other
 

---

 
Select any who the proposed effort intends to benefit most.
Choose region
 
- [x] Global 
- [ ] North Africa and Middle east 
- [ ] East Africa 
- [ ] West Africa 
- [ ] South Africa 
- [ ] North Asia and Russia 
- [ ] Central Asia 
- [ ] East Asia 
- [ ] South Asia 
- [ ] South-East Asia 
- [ ] Eastern Europe 
- [ ] Central America 
- [ ] Caribbean 
- [ ] Andean 
- [ ] Southern cone 

---

 
## Why is this project needed?
*Content limited to 2000 characters - Describe one or more of the following: the specific needs of the group(s) being met, how it uniquely solves a known issue or improve upon existing solutions, and/or what knowledge, research, technology, or community gap the proposed effort is intending to fill. If the effort targets a specific group of people, note any research or analysis you have done to ensure the effort serves the target population.*

The legacy approach to data (passwords and data backups) does not map well to existing human patterns. Bill Gates declared the password dead in the 00's. We think he was onto something but his conception of the alternatives has been limited and enclosed behind a fortress mindset. 

*   Encryption tools have been around for a long time but are still only used by a minority (research which shows this?).  We think the problem of private key custody is a **major barrier to accessibility**. 

* Traditional methods of backing up keys or passwords require either hardware devices (which not everybody has, and which can also easily be lost) or relying on a trusted third party (which might become unavailable or untrustworthy).

* Our experience of running workshops where we helped people set up and use password managers has brought to our attention a whole range of issues and barriers.  These problems are of particular concern to users who have difficulty making regular backups due to limited hardware, a distrust in centralized service providers, a chaotic lifestyle or vulnerable housing situation.  (go into more detail about this research)

* The emphasis on each individual taking responsibility completely and exclusively for themselves is a reflection of western individualist culture.  We believe some people find this alienating and this poses a **cultural barrier** to much needed technologies. 

* We propose an **offline-first system**.  While internet connectivity in generally improving worldwide, **net neutrality** is an increasing issue in many countries. As well as issues with government censorship and surveillance, in many countries mobile internet providers are increasingly offering connections limited to only a few specific commercial services (such as facebook). Mobile internet connections are relied upon more by people who are poorer, have housing issues, or do not have access to banking. (explain with research)

* In order to test the usability of existing implementations of Shamir's secret sharing we conducted a role-play experiment where we assumed two members of our group had been incapacitated due to being hit on the head with coconuts.  The remaining group members had to reconstruct their secrets.  We found that this is a considerably harder problem to solve than that of an individual wanting to recover a lost secret themselves.  We identified many issues that made things confusing and impractical and the design of our project is a response to these findings.  




---

## Addressed problems *
*Select any of the most prominent and appropriate problems that the proposed effort seeks to address.*

- [ ] Restrictive Internet filtering by technical methods (IP blocking, DNS filtering, TCP RST, DPI, etc.) 
- [ ] Blocking, filtering, or modification of political, social, and/or religious content (including apps) 
- [x] Technical attacks against government critics, journalists, and/or human rights organizations (Cyberattacks) 
- [ ] Localized or nationwide communications shut down or throttling (Blackouts) 
- [x] Physical intimidation, arrest, violence (including device seizure or destruction), and death for political or social reasons 
- [ ] Pro-government manipulation of online discussions (propaganda, imitation content, and/or sockpuppets) 
- [x] Repressive surveillance or monitoring of communication 
- [ ] Policies, laws, or directives that increase surveillance, censorship, and punishment 
- [ ] Government practices that hold intermediaries (social networks or ISPs) liable for user content 
- [x] Prohibitive cost to access the Internet 
- [ ] Other 


---

## Similar/Complementary efforts 
*List other similar efforts to this proposed project. OTF expects this to include a review of any available technologies or programs that are similar to the project described. This not only allows OTF to understand how your project can be distinguished from those already active but also an applicantâ€™s understanding of the current landscape for such an undertaking.*

* 'Conventional' **locally installed** password managers such as keepass rely solely on the user making their own physical backups.  Data security and integrity is only as good as the individual user's hardware and backup routine. 

* Password managers which work in combination with a **trusted third party** cloud service such as 1Password, Lastpass, Dashlane.  This improves data integrity but there are issues with privacy and accessibility. 

* **Deterministic password managers** such as MasterPassword (https://masterpassword.app/) work by generating a single master key from a primary password combined with another source of entropy such as the user's name. An unlimited number of passwords can then be derived from this key meaning the user only needs to remember a single password. This solves the problem of needing physical backups and gives resiliency to device loss.  But this method does not work in the case of the user becoming incapacitated or loosing the master password.  Furthermore, there are great security issues if the master password is compromised. They also cannot be used for existing secrets or keys, making them impractical for many of our indentified use-cases.

* **Full-featured secret management tools** such as Vault by HashiCorp (https://www.vaultproject.io/) solve a lot of the security issues we have identified but are intended for enterprise use, which brings accessibility issues.

* **Existing implementations of shamir's secret sharing** such as PassGuardian and dyne.org 'secrets' give a community based solution, but lack features which automate the transmission,storage and retrieval of shards making them cumbersome to use.  

* Encryption use has recently become much more widespread due to the advent of encrypted **mobile messaging** software.  While these tools have undoubtably drastically increased accessibility, they remain dependent on centralized service providers which can be influenced or even banned by oppressive governments. Furthermore, in case of device loss or theft, identity is generally determined by the presence of a **hardware token** (SIM card) which are issued and revoked by a centralized service, giving governments further opportunities to intervene or gain personal data.

---

Other information 
Content limited to 2000 characters



http://darkcrystal.pw
- Client plugin: https://github.com/blockades/patchbay-dark-crystal
- API:  
- Protocol schema: https://github.com/blockades/ssb-dark-crystal-schema

+ our email addresses + ssb identities

Secure scuttlebutt: https://www.scuttlebutt.nz/ #mmt and #dark-crystal channels.

We could possibly also add here a simple explanation of shamir's secret sharing?
