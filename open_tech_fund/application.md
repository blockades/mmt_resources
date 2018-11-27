# Open Technology Fund

## What is your project name? 
Dark Crystal

## What is your idea?
*Describe it - Content limited to 2000 characters*
 
Dark Crystal takes a novel approach to using Shamir’s Secret Sharing algorithm, combining narrative, community, and ritual with new peer-to-peer (p2p) technologies to achieve distributed secret persistence. A working prototype application has been built on the Secure Scuttlebutt stack, a p2p offline-first gossip protocol, database, and mesh network. 

On Scuttlebutt, records in a local append-only database are replicated between peers across a network up to *n* degrees of separation, providing uncompromising data resilience. Encrypted data can be recovered from the mesh without ever exposing its contents.

We posit that this persistence model is transformative when applied to the wicked problem of secure key management. In its prototype form, Dark Crystal extends the Scuttlebutt ecosystem, enabling peers to securely back up secrets (private keys, passwords, or other sensitive information) by harnessing the trust in their social network.

A user’s secret is split into ‘shards’, encrypted with the relevant Ed25519 keys, and sent to selected peers. If the user's identity becomes compromised, they get locked out, or they lose their secret, their peers can recombine the shards to recover it. Should they need to regain access, the user requests the shard back from each custodian, only exposing the original secret once proof of identity is achieved and the user-defined quorum is reached. Dark Crystal makes this process simple—much simpler than existing sharding tools—minimising human error and increasing accessibility. 

We believe this social model of data custody has many implications and use-cases. It is a critical tool for journalists or activists who need to reliably distribute sensitive information, such as the key to an encrypted cache of documents. It removes reliance on single points of failure, such as hardware devices, trusted authorities, or service providers (and even internet connectivity). With Dark Crystal, your peers become your secret layer of persistence.

Character Count: 1993

---

## What are hoped for goals or longer term effects of the project?

*Content limited to 2000 characters - We want to know how you think the world could be, what larger purpose this project is a part of, and/or the bigger target you aiming for. Bulleted lists are good.*

- The difficulties of private key custody is an ever-increasing problem in encryption and digital identity. We want to solve it using the power of community networks and human trust. 

- We believe Dark Crystal can make encryption tools more accessible, helping journalists or activists maintain security and access if they lose their computer, become incapacitated, or are captured.

- Enable custody of a sensitive document or piece of information to be distributed among a trusted group, in such a way that the group must agree together if and when it is safe to reveal it. 

- Create a storage solution for sensitive documents that would allow the carrier to cross international borders without having either the keys or the documents on their person, without relying on any company, cloud, or specific hardware, such that they are able to recover the documents at will when the time is right.

- Build a system of sharing custody of secrets that works independently of any third party or authority, and even of having an internet connection. This has big implications for people living in regions with poor connectivity or net neutrality issues.

- Replicate the protocol across different distributed systems, extending the practice to a broad base of beneficiaries.

- By emphasising trust in the tools we use, we can instill a sense of community and cooperation. We want to empower groups of trusted peers to take control of their own security together.

- We are a feminist, social justice oriented group, and we speak out about our values. We are privileged to be able to wield p2p tech, and understand this is not the case in many parts of the world. We want to widen the scope of who gets to be a peer in p2p. We believe the decentralised web (3.0) is the future of technology, and it's critically important that everyone gets to participate.

Character Count: 1839

--------

— Our research into the accessibility of cryptographic tools found the unforgiving nature of key custody (i.e. unrecoverability) presented a serious barrier, especially for those less experienced with this type of technology. Security and accessibility are often in tension. Making sharding a smooth and simple process can enable more people to significantly increase security of their important secrets.

Character Count: without last point: 1839 with it: 2180


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

0. Dark Crystal v1.0 - Already complete
- Conduct research among our peers through open workshops, discussions and trials of alternative apps

- Build and release working prototype and begin user testing

1. Dark Crystal v1.5 - 2 months
- Test prototype with varied user base, emphasising accessibility

- Integrate feedback from testing and research 

- Improve the user interface and community interface

- Port application into most popular and easy to use SSB client (Patchwork)

- With support from visual designers, create stellar, easy to understand documentation

Budget: $60,000

2. Dark Crystal v2.0 - 6 months

- Build standalone application that functions independently of other SSB clients

- Enable use case: Shard custodians can recover secret without original user's involvement in case of incapacitation, death, or compromised/lost identity

- Implement feature to acquire consent for custody of a shard in-band

- Integrate with popular encryption tools such as GPG

- Efficient storage and recovery of larger secrets and files

- Internationalization to broaden access

- Attach set of instructions (eg: a will) to a shard, to provide more information to custodians

- Commence research into mobile app version of Dark Crystal, in collaboration with MMMMM, a prototype Android SSB client

- Research other mobile implementations to improve access

- Research and trial application with allied international groups

- Initial launch and publicity to NGOs and activist groups

Budget: $150,000

3. Research and maintenance - 4 months

- Integrate results of trials with target groups. Implement support for specific use cases (specialised documentation, technical implementations, user workflows)

- Integrate research and feedback into application

- Publish white paper compiling research, the protocol, and its application

- Build Android client, either stand-alone or port into MMMMM 

- Investigate portability of protocol into other p2p ecosystems to broaden user base

- Official launch, further targeted publicity

Budget: $90,000

Character count: 1998


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
                                      
* **Anyone using encryption** will benefit greatly from improved key integrity. We plan to implement features to integrate with GPG for handling private keys and revocation certificates.

* **Anyone at risk of losing a computer or device**, or those who do not have a secure methodology to store important data--people seeking asylum, at-risk journalists, people crossing borders, and activists.

* **Anyone living in an oppressive regime**, who has custody of sensitive information and is concerned for its resilience. A journalist or activist with critical information might want to give their passwords/keys to a trustee in case they are captured, but this could endanger that person. By distributing encrypted shards, which by themselves nothing about the secret, Dark Crystal removes the single point of failure by enabling a quorum of peers to collectively decide if and when it is safe to reveal the secret.

* Anyone with **poor or no internet connectivity**. Dark Crystal is an offline-first p2p application, which can function independently of the internet. Furthermore, the SSB gossip protocol allows the spread of information between peers with internet connectivity and those without, by syncing devices which move between physical locations (sneaker net).

* **Those in need of political asylum** are often unable to carry sensitive documents that may be required later as evidence for an asylum claim, for example when crossing certain international borders. By securing a document's encryption key (or the information itself in text form) with Dark Crystal, the information can be recovered when they need it, without having to transport the documents themselves.

* The notion of **trust within a small community** of people is a concept that is well understood and endorsed by people from a wide variety of cultures. Individuals themselves are the best judges of who to trust in their unique context, and Dark Crystal puts that choice in their hands alone, without the need for an intermediary company, server, or authority.

Character count: 1997

---

Content limited to 2000 characters. 

## What community currently exists around this project?

Define the community as you see it. If your answer is none, please explain how you plan to cultivate community around the proposed effort, including mechanisms to receive feedback and get others involved.

---

Our backgrounds and passions are in activist communities and high-trust networks. We believe that development of new technologies must be rooted in communities, not applied as an abstract solution to a perceived problem. We organise and communicate in public on Scuttlebutt (SSB), a cryptographic social network and messaging protocol. All development has stemmed from real-world experience and research, and is completely open source.

Our working prototype is currently being trialled by members of the SSB community. This community spans six continents and is reminiscent of early internet forums, before spam and distrust. It is difficult to estimate the number of SSB users. A recent study revealed a minimum of 7000 users. Although Dark Crystal can be used by anybody independent of this community, SSB is an excellent base for user testing, and a broad forum from which to source feedback.

Our team began with an inquiry into how to make cryptographic tools more accessible. After hundreds of hours of education sessions and interviews, key custody emerged as a critical barrier faced by diverse users, especially more marginalised groups with intersecting challenges. We maintain strong links to these early testers, and we are building Dark Crystal with them in mind.

We consider ourselves a feminist group, and have links with feminist and LGBTQIA activist groups internationally. We are currently conducting a survey of groups in Russia and Belarus to establish which encryption tools they use, what problems they have encountered, how they back up their keys, and why they don't use encryption if they would like to.  This research will influence development, and broaden our userbase.

To offer a useful tool to users living under oppressive regimes, journalists, activists, asylum seekers, we are focused on making the on-boarding process and user experience as simple as possible. Future development will minimise language and culture barriers and focusing on accessibility.

Character count: 1995

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


*   Encryption tools have been around for a long time, but they are still widely misunderstood and only used by a minority. Our research has shown that the problem of private key custody is a major barrier to accessibility.

* Traditional methods of backing up keys or passwords require either hardware devices (which not everybody has access to, and can be easily damaged or lost) or relying on a service provider or trusted third party (who may become unavailable or untrustworthy).

* Our experience of running workshops assisting people to set up and use password managers revealed a whole range of issues and barriers. These problems are of particular concern to users who have difficulty making regular backups due to limited hardware, a distrust in centralized service providers, a chaotic lifestyle, or vulnerable housing situation.

* The emphasis on each individual taking responsibility completely and exclusively for themselves is a reflection of an individualistic culture.  This can be alienating and poses a cultural barrier to much needed technologies. People already managing a lot of risk and interacting with unforgiving processes in their lives might not want to take on more.

* Existing tools using Shamir's Secret Sharing are woefully under-developed and hard to use, involving copying and pasting long alphanumeric strings, figuring out how to share them securely, making sure trustees know how to securely store and back them up, and manually recalling them. We have not found a user-friendly application.

* Dark Crystal takes an offline-first approach. The ability to replicate data across a LAN network or Bluetooth connection ensures secure secret backup beyond the confines of the internet. Net neutrality is an increasing issue in many countries, as well as issues with government censorship and surveillance. Dark Crystal enables peers to back-up sensitive information without reliance on ISPs, circumventing remote surveillance and censorship.

Character count: 1991

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
*List other similar efforts to this proposed project. OTF expects this to include a review of any available technologies or programs that are similar to the project described. This not only allows OTF to understand how your project can be distinguished from those already active but also an applicant’s understanding of the current landscape for such an undertaking.*

* 'Conventional' **locally installed** password managers such as keepass rely on the user making their own physical backups. Data security and integrity is only as good as the individual user's hardware and backup routine.

* Password managers which work in combination with a **trusted third party** cloud service such as 1Password, Lastpass, Dashlane depend on an internet connection, availability of the service, and the third party remaining trustworthy.

* **Deterministic password managers** such as MasterPassword (https://masterpassword.app/) generate a single master key from a combination of a password and two other sources of entropy, which solves the issue of persistence but requires a consistent methodology that many users find complicated. In the case of torture or compromised security, revealing the methodology exposes not just one but **all** secrets. The individual remains the single point of failure.

* **Existing implementations of shamir's secret sharing** such as PassGuardian and dyne.org 'secrets' lack features to automate the transmission, storage, and retrieval of shards, making them prohibitively complex and cumbersome to use. 

* Encryption use has recently become much more widespread due to the advent of encrypted **mobile messaging** software.  While these tools have undoubtedly drastically increased accessibility, they remain dependent on centralized service providers who can be influenced, or even banned, by oppressive governments. Furthermore, security can be compromised in case of device loss or capture, since identity is generally determined by a **hardware token** (SIM card) issued and revoked by a centralized service. This hands repressive governments and bad actors further opportunities to intervene or gain access.

Character count: 1768 

---

Other information 
Content limited to 2000 characters

**Website:**

http://darkcrystal.pw

demo gif:
http://darkcrystal.pw/img/screencast.gif

**Code:**
Client plugin / UI: https://github.com/blockades/patchbay-dark-crystal
API:  http://github.com/blockades/scuttle-dark-crystal
Data schemas: https://github.com/blockades/ssb-dark-crystal-schema

**Contact**
dh@blockades.org
ameba23@systemli.org
kieran@tenthousandthings.org.uk
mix@enspiral.com
hello@alanna.space

+ our email addresses

Secure scuttlebutt: https://www.scuttlebutt.nz/ #mmt and #dark-crystal channels.


notes from Alanna:

I made a bunch of tiny grammar and punctuation changes, so the character counts should probably be re-checked.


"Storing and recovering large secrets; file encryption" --> this makes it sound like it's not encrypted in v1.0 & 1.5, but it is?

Unclear if the tick boxes are select one or select many....

"We plan to implement features to integrate with GPG for handling private keys and revocation certificates." --> if so, this should be somewhere in the roadmap, right? Or is that post research and maintenance phase?

Under "What community currently exists around this project" should we also mention a) advisors, partners, and collaborators and b) our connection to people/orgs who could help get DC to those who need it? ex. I have connections to UNICEF, Amnesty Intl, one hop from Glenn Greenwald, etc. I'm sure we each have valuable networks.

Under "Why is this project needed?" - add a point about why encryption itself is becoming more and more important in our current world.

Under "Similar/Complementary efforts" -- what's here is a good summary of the software landscape, but step back and ask what are the people mentioned in this application (journalists, asylum seekers, etc) actually using instead of Dark Crystal now? Some of the answers might be software, but others might be physical documents, telling friends sensitive info, etc. Maybe think a bit broader about our real "competators". For example, the competator to password managers is post-it notes and password reset functionality.

If I were judging these applications, I would also be wondering about credibility and skills to deliver on this. E.g. past success building and releasing useful applications, marketing and communications, successful team coordination, etc. Is there somewhere this kind of stuff fits? Basically, we've done startups before and we've been around the block a bit.

