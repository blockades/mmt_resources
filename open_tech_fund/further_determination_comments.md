## Goals and principles

### We found the proposed project with OTF's remit and appreciated the application focusing on the potential benefits to at risk communities. Nonetheless, while the application pointed to those who have "difficulty making regular backups due to limited hardware, a distrust in centralized service providers, a chaotic lifestyle, or vulnerable housing situation", it did not detail specific instances in which existing password managers have been comprised or otherwise jeapordized the safety of those in repressive environments. How much additional value does the solution proposed add to existing password managers? We have generally found that user behavior is a more common point of failure with regard to password managers than a centralized storage design. Please provide more information in this regard.


Our conversations and research over the past 12 months have shown there are a collection of intersecting concerns when thinking about the wicked problem of secure private key or password management that cannot be individually extrapolated into isolated solutions. To summarize, we've narrowed these down to three primary categories: connectivity, data security / cloud integrity, and personal responsibility. It is our understanding that peer-to-peer technologies combined with interpersonal trust with affinities go a long way to addressing these concerns for the use cases described.

For password managers reliant on local storage (such as KeePass), there are a number of situations that somebody in a repressive environment might face which could result in data loss or a security breach. These include a device being seized, device loss due to having to flee one's home and hardware failure due to poor conditions or inadequate hardware. 

Password managers backed up by external cloud services get around these problems, but are dependent on reliable, secure connectivity to the provider, as well as users' trust in the provider.  Barriers to these are connectivity issues, government surveillance, and censorship of particular services. The internet blackouts in Syria in recent years (whether due to poor infrastructure or state intervention) are a good example. The Opennet initiative, although it stopped conducting research in 2014, has detailed country by country reports on internet surveillance and censorship, many of which are alarming.

We agree, and our research reinforces this, that user behavior is a common point (possibly the primary point) of failure regarding password managers. We have observed in case studies and taught in our workshops the use of centralized cloud service providers for persisting a password database. We have also experimented with using centralized password service providers. Dark Crystal takes a different approach towards genuine authentication. Using centralized password managers and/or cloud service providers (which enable access without dependent hardware) opens up the possibility of the exposure of encrypted data by way of deception. In a scenario whereby a person becomes compromised, access to private keys / passwords can be gained through the front-door using either password reset or an official identifier such as a passport. It is paramount to mention centralized services are major targets of back-end hacks and can be subject to data breaches.  For example, OneLogin, a password manager for enterprise users used by 2000 companies worldwide, was was subject to a major security breach in 2017 and cloud storage service Dropbox was hacked in 2012. 

A recent study by the Frauenhofer Institue for Secure IT performed a security analysis of the most popular Android password managers by download count, each of which had between 100,000 and 50 million downloads.  Of nine password managers they found 26 security flaws, including major implementation flaws, such as the master password being stored as plain text, or the use of hard coded cryptographic keys in the program code. Such vulnerabilities become considerably more serious in the case of password managers backed by cloud services (which the majority of them were), as there is a danger of data being exposed globally rather than only to those with physical access to the device.  Those working in oppressive environments are perhaps not at considerably more risk from these vulnerabilities than other users in general, but the consequences of leaking information which implicates them can be considerably more sinister.  

We do not argue that we are able to build a tool which has no vulnerabilities whatsoever, rather that the topology of the system has a substantial effect on the risks associated with such vulnerabilities.  Storing sensitive information in a single centralized location gives a specific target for attacks, and a single point of failure.  Distributed systems overcome this problem.

Dark Crystal's approach roots user / person authentication and thus access to the encrypted data through the relationships said person holds. This model draws from other approaches in the field, such as Keybase, who attempt to solve the issue of authentication by building an ecosystem of distributed verified references to a single identity. Dark Crystal was inspired by Keybase's approach but applies authentication in the context of peer-to-peer technology, whereby authentication is based on existing relationships with people. This is significantly more powerful for data preservation and security, fosters interdependence and a networked knock-on effect. 

Our research has indicated that lack of trust in a provider, or lack of knowledge of a trustworthy provider, is a major barrier to the use of third party cloud services for backing up cryptographic keys.  When dealing with keys for particularly sensitive information, people become even more cautious.  Even when a provider is known to be trustworthy and secure, phishing techniques or intercepted packets can pose a security risk. 

Although we've made comparisons to and done research related to password managers, our proposed tool solves a different problem to that of a password manager.  Firstly, it is designed specifically with cryptographic key management in mind.  Although some password managers can handle cryptographic keys, and there exist other tools and services for key management, individuals and organizations dealing with encryption keys for sensitive information tend to backup keys on servers which they control or hardware devices which they own rather than using a third party service (according to the 'Global encryption trends study'). Unfortunately, not everyone has access to such resources, and this is an issue our tool addresses.   

Furthermore, our tool is better suited to long-term backup of sensitive data rather than everyday storage and retrieval. This is because one has to wait for a human-initiated response from several peers in order to retrieve shards, whereas password managers typically retrieve data in a matter of seconds. This gives additional security at the cost of being time-consuming to retrieve. Depending on the user's individual security needs, our tool could be used to backup the database of locally installed password or key management software.  But for particularly sensitive data, or precarious situations such as traveling in a dangerous area or crossing a checkpoint or border, we would not recommend keeping a local copy of the secret.

#### References: 
- Password manager 'OneLogin' hacked in 2017 https://www.zdnet.com/article/onelogin-hit-by-data-breached-exposing-sensitive-customer-data/
- 'OneLogin' used by 2000 companies worldwide https://www.crunchbase.com/organization/onelogin#/entity
- Dropbox 2012 security breach https://motherboard.vice.com/en_us/article/nz74qb/hackers-stole-over-60-million-dropbox-accounts
- Opennet initiative https://opennet.net
- Global Encryption Trends Study, 2018, The Ponemon Institute sponsored by Thales Security https://www.thalesesecurity.com/2018/global-encryption-trends-study
- Security analysis of password manager apps by Team SIK of the Frauenhofer Institute for Secure Information Technology, 2017  https://team-sik.org/trent_portfolio/password-manager-apps/
- Keybase, a key directory that maps social media identities to encryption keys in a publicly auditable manner. https://keybase.io/


### Please provide any ouput reports or associated materials related to your "inquiry into how to make cryptographic tools more accessible" through "hundreds of hours of education sessions and interview" identifying key custody as a critical barrier faced by at-risk users. We are keenly interested in the research that led to this use case being considered of highest priority.

Our report on accessibility of cryptographic tools 
https://github.com/blockades/mmt_resources/blob/master/research/accessibility_of_cryptographic_tools.md

A Github repository containing research compiled in writing:
https://github.com/blockades/mmt_resources/tree/master/research

### Reviewers found the underlying technology to hold promise yet were not convinced of the need for a password manager with the specific set of features described. As such, please explore the benefits and drawbacks of the project focusing on advancing the usability and functionality of sharding technology as compared to doing so with the express purpose of creating a specific user facing tool.

Although Dark Crystal can be used for backing up passwords, and we have made comparisons with and taken inspiration from password managers, Dark Crystal isn't trying to be a next-generation password manager. The focus of Dark Crystal is to open access to software where users gain independence by taking responsibility for keys securing their identity.  This covers encryption tools as well as p2p offline-first protocols for secure social communication, for communities needing to share sensitive information without the added dependencies of hardware devices, trusted authorities, and/or centralized service providers. The price of entry to using these technologies, which have great potential to provide uncensored and unmediated communication, is being able to keep local keys secure and accessible. It is important to note that many password management service providers aren't designed, not should be relied upon or used, to secure private encryption keys, and many users we spoke to said they would not trust a cloud service with their encryption keys.

The application of sharding technology applied on-top of a social gossip protocol is particularly powerful.

Benefits of sharding technology in this context
- Well suited for storing and recovering GPG keys and revocation certificates, keys for disk encryption software, SSH keys or any other type of data which can be regarded as too sensitive to be kept in custody of a single party.
- The quorum of required shards allows for the secret holder to make a trust determination based on the peers involved, they can choose to set a low or a high bar to trust based on the circumstances. As such it is adaptable to differing scenarios.
- Sharding within a social network gives a small community a secure backup solution using minimal resources and infrastructure.
- Well suited for recovering SSB identities, which allow for replicating data from peers. Enables someone to recover an identity from their friends / peers, and all encrypted data associated with that public / private keypair (also from their peers), due to lost hardware or other causes.
- Secret sharing schemes, as described by Shamir and Blakley, are probably information-theoretically secure. That is to say the individual shards hold no semantic information about the secret. The root key for ICANN DNS security, effectively the key which secures the naming system of the internet, is held by seven parties, based in Britain, the U.S., Burkina Faso, Trinidad and Tobago, Canada, China, and the Czech Republic. Cryptographer Bruce Schneier has alleged that they are holders of Shamir's secret shares which would indicate that the scheme is considered to be secure.
- A second level iteration (sharding a shard) is possible and in theory, with a peer-to-peer system, not impractical to implement. This is something we would like to explore, as it could mitigate an attacker's attempt to sabotage exposure of a secret by adding a nested layer of resilience to each shard. This could function much like a phone-tree, alerting peers of a set of circumstances.

Drawbacks
- Sharding is a community-focused solution. It is not suited for isolated individuals surrounded by a hostile environment.
- The quorum of required shards represents a trade-off between data persistence and security. It can be difficult to decide an appropriate value.  Requiring too many shards means there is a danger that the secret can be lost if some shardholders become unavailable.  Requiring too few decreases the number of shards required by an attacker to gain access to the secret.
- It requires some knowledge and understanding of the technology.  Explaining the concepts, as well as gaining consent from shardholders can be time-consuming.  
- Some people feel uncomfortable with the responsibility of holding a shard for someone else.  While we have found this is greatly reduced when they understand that if they lose the shard there are still enough others to reconstruct the secret, and that the shard itself contains absolutely no information about the secret, this may remain a barrier. 
- As noted above, retrieving shards, in the given context, requires waiting for a response from human actors, which makes it considerably more time consuming to use compared with automated backup solutions.  Therefore it is not suited for storing information which might be needed urgently.

#### References
- Shamir, Adi (1979). "How to share a secret". Communications of the ACM. 22 (11): 612–613. doi:10.1145/359168.359176.
- Blakley, G.R. (1979). "Safeguarding Cryptographic Keys". Managing Requirements Knowledge, International Workshop on (AFIPS). 48: 313–317. doi:10.1109/AFIPS.1979.98.
- Beimel, Amos (2011). "Secret-Sharing Schemes: A Survey" http://www.cs.bgu.ac.il/~beimel/Papers/Survey.pdf
- Schneier, Bruce (2010) - DNSSEC Root Key held by 7 parties worldwide https://www.schneier.com/blog/archives/2010/07/dnssec_root_key.html
   

## Technical merit
### It was not clear to reviewers how the project would overcome the inherent challenge with peer based trust systems which require substantial adoption for the full functionality to be achieved. Furthermore, while distributing sensitive information through a trusted network protects the information from centralized service providers, it also has the potential to implicate this trusted network should the government seize their devices. We would also like to see more information on why the underlying Scuttlebutt network is the most ideal p2p network for this, the motivations for choosing this network, and the pros/cons. In addition, we would like a deeper understanding of the extent the scuttlebutt aspects would be useful to other projects relevant to OTF's focus areas and its current level of maturity. Please include more information as to how these challenges would be addressed.


#### Substantial adoption needed for full functionality

Full functionality of our tool can be achieved without substantial adoption of the protocol (although the protocol is indeed being ever more widely adopted).  It is possible for any group of people to successfully use our tool regardless of the extent to which the protocol is widely adopted. Of course, there are great benefits to being connected with many peers in terms of data replication, but the functionality of our tool does not depend on this. We have successfully used our tool on a test network with only the number of peers required for the test (link below).

That said, we appreciate that there are many peer-to-peer protocols and that a small initial user-base may create limitations.  However we believe that SSB has properties which make it particularly suitable for our use case (detailed below) and that these benefits are greater than those we would gain by using a more popular protocol. 

#### Implicating shard-holders in the case of device seizure 

This is a deep concern and an area we are approaching with much caution.  Depending on the level of security required, there are several possible features which could improve security in this case.

At the user interface level, shard-holder names could no longer be displayed after the shards are sent. Many users will value the convenience of seeing a reminder of who they sent shards to, but this is not a hard requirement because even if they forget, they can still request return of the shards in order to retrieve the secret, and these requests will be sent to shard-holders.  That is, shard-holder identities are remain stored, but are hidden from view in the user interface. 

At the database level, shard-holder public keys could no longer be stored. This would require the secret-holder to remember who they sent the shards to in order to request them back. In this case, if the device was seized and the secret-holder's private key compromised, the identities of the shard-holders would remain unknown. 

This is possible because the encryption mechanism that SSB uses obfuscates message recipients. Contrary to, for example, GPG encrypted email, on SSB there is no way of seeing who an encrypted message is being sent to without decrypting it. This brings great benefits to security but it comes at a cost, as it means that in order to receive an encrypted message, one must attempt to decrypt all available messages.  This would be totally impractical to do with a traditional network topology, as there would simply be too many messages.  But on SSB, one is only exposed to a subset of all messages on the network based on relationships between peers.

It is also worth noting here that the shard-holders themselves do not necessarily need to know who each other are.  We have designed a feature whereby in the case of the secret-holder being incapacitated and the shard-holder identities unknown, a shard-holder can broadcast a message containing a hash derived from the key of the root message unique to the secret, in order to make contact with the other shard-holders, and a cryptographic handshake can be used to verify that they do indeed hold an associated shard. 

We are also considering a system similar to GPG revocation certificates whereby an identity can be revoked (and no longer deemed trustworthy) upon publication of a signed certificate.  This could potentially be utilized in the case of capture or device seizure or loss.

#### References: 
- Our API tests https://github.com/blockades/scuttle-dark-crystal/tree/master/test
- private-box repository README provides a good explanation of recipient obfuscation https://github.com/auditdrivencrypto/private-box 

#### The motivations, pro and cons of SSB over other p2p networks for this project

Contrary to content-addressed systems like Bittorrent, IPFS or DAT, SSB is structured around propagating 'feeds', collections of messages from particular peers, based on the relationships between peers. As such, a particular piece of data is not either 'on SSB' or 'not on SSB', rather the data held by each peer depends on their relationships with other peers. The network topology is determined by social topology. These fundamental properties make it ideal for sharing sensitive information within a limited group.

Many other peer to peer systems we considered use a distributed hash table (DHT) to index and propagate data.  SSB uses a gossip protocol. With a DHT, all users have, in principle, access to a ubiquitous data-set, and their connectivity with particular peers effects only how long it might take to find a particular piece of information (of course in practice some data often cannot be retrieved).  In that sense it essentially emulates the behavior of a centralized system, where all users access the same source of data.  By using a gossip protocol, the data-set itself is dependent on the relationships between peers.  In the case of scuttlebutt, the user explicitly chooses which peers they want to relate to, and by doing so retrieves messages from those users' 'feeds', regardless of their content, and stores them allowing them to propagate to other peers requesting messages from that particular user.  As such, it has a relationship-centered topology. 

There is much discussion about the optimal parameters for 'gossiping'. Notably, the 'number of hops', the extent to which a user holds data from indirectly related peers ('friends of friends', or 'friends of friends of friends'). This can be individually adjusted using client software and might vary depending on the use-case, the resources available and the attitude of the user.  Clearly, there is a trade-off between security and data persistence, and this is something we would like to investigate further. The important distinction is that the characteristics of gossip protocols are best suited for relationship-centered applications whereas DHTs are better for content-centered applications.

Of course, SSB is not without its limitations. IP addresses are exposed by default. There are ways around this, but it is important to note that it is not anonymous out of the box.  That said, the handshake mechanism used has some promising security properties. It is impossible to connect to a peer without knowing their public key, and peers have control over who they allow connections with. Passive eavesdroppers exposed to the handshake are unable to determine the public key of either peer. 

SSB is also not well suited to handling large files and data sets.  Messages in SSB feeds are limited to 8kb, and larger amounts of data such as images and other media are handled by a distinct sub-protocol called SSB-blobs.  However, SSB-blobs is also not designed for particularly large data sets (by default, 'blobs' are limited to 5MB).  Because of this, as well as the fact that secret sharing schemes are themselves not well suited to particularly large data sets, for larger secrets we propose to use SSB to handle only encryption keys, and the encrypted data itself is stored by other means such as DAT. 

#### References:
- Robbert van Renesse, Dan Dumitriu, Valient Gough, and Chris Thomas (2008). Efficient Reconciliation and Flow Control for Anti-Entropy Protocols. (Good description of a gossip protocol) http://www.cs.cornell.edu/home/rvr/papers/flowgossip.pdf
- Tarr, Dominic (2015) Designing a Secret Handshake: Authenticated Key Exchange as a Capability System (This is the principle security mechanism used by SSB) http://dominictarr.github.io/secret-handshake-paper/shs.pdf
- The DAT project whitepaper  https://github.com/datprotocol/whitepaper/blob/master/dat-paper.pdf
- Maymounkov and Mazieres (2002) "Kademlia, A peer to peer information system based on the XOR metric" (A good description of distributed hash tables) https://pdos.csail.mit.edu/~petar/papers/maymounkov-kademlia-lncs.pdf
- SSB-blobs, a sub-protocol for gossiping 'blobs' https://github.com/ssbc/ssb-blobs

#### A deeper understanding of SSB and how it might be otherwise relevant to OTF's focus areas 

SSB is a relatively young protocol.  The initial commit was made in 2012 and the first message to what is currently the predominant network was published in 2015. The exact number of SSB users is unknown but there are at least 8,000 known accounts.  It has been described as "how the internet used to be" perhaps because it is slow and is used by a friendly and trusting community.  

SSB's 'feeds' can be thought of as a diary for each peer.  The diary is an append-only log of hash-linked signed messages consisting of javascript objects.  Each peer stores and regularly synchronizes the diaries of other peers with which they have relationships, as well as of peers on the periphery of their social network, depending on the desired number of 'hops'. Depending on the application, messages of particular types or with particular properties are aggregated in different ways, typically using a custom-built database and query system, flume. 

Due to the need to continually process multiple feeds, SSB applications tend to make heavy use of streams.  A custom system of pipeable streams has been developed which is particularly suited to processing SSB feeds.  

- pull-stream, minimal pipeable pull-streams https://pull-stream.github.io/
- flumedb, a modular database 'for moving logs with streams' https://github.com/flumedb/flumedb
- ssb-query, an index for flume views specifically for scuttlebutt https://github.com/dominictarr/ssb-query
- ssb-backlinks, a commonly used module for aggregating links to a common root message https://github.com/ssbc/ssb-backlinks

SSB's offline-first nature combined with the social topology provided by the gossip protocol gives some properties that make it particularly suited to communities in remote areas with poor connectivity.  If one community member travels with their device to a neighboring community or town, they carry with them the message feeds of members of their extended social network, including encrypted messages which they have no access to themselves.  Upon connection with other peers, there is a mutual exchange of newer messages, meaning they bring news both from and to the community, without having to take any explicit action themselves.  

As SSB is a new protocol quickly gaining popularity, it makes sense to consider how well it scales.  It could be that the protocol performs well with thousands of users, but not so well with millions.  A paper on scalability of the scuttlebutt network is currently in progress which outlines some optimizations to reduce unnecessary replication and makes comparisons to other models.  While things look very promising in theory, it is of course based on certain assumptions and it is impossible to know what might happen in practice. 

Mozilla Firefox has added support for the ssb:// extension earlier this year (along with DAT and IPFS) https://blog.mozilla.org/addons/2018/01/26/extensions-firefox-59/

There are strong links with and a crossover into the DAT developer community.  The two systems can be seen as complementary.

Noteworthy applications on SSB include: (Complete list: https://www.scuttlebutt.nz/applications )
- Patchwork, the most popular and stable client 
- Patchbay, less polished and more hackable, with some interesting features
- Patchfox, an ssb client as a firefox extension
- Patchfoo, a minimal UI designed for low resource computers
- Multiverse, a beta android ssb client
- git-ssb, decentralized git repository hosting 
- ssb-polls, a group decision making tool (like loomio)
- Ticktack, a blogging platform
- ssb gatherings, an events listing system 
- a calendar invites system (like doodle)
- ssb-npm, a decentralized npm registry
- ssb-chess 

#### References and media articles:
- The Scuttlebutt Protocol guide (a detailed description of the protocol) https://ssbc.github.io/scuttlebutt-protocol-guide/
- 'Scalable Secure Scuttlebutt' (draft) https://github.com/dominictarr/scalable-secure-scuttlebutt/blob/master/paper.md 
- 'The Atlantic' article 'Meet the nomad who's been exploding the internet into pieces' https://www.theatlantic.com/technology/archive/2017/05/meet-the-counterantidisintermediationists/527553/
- Cory Doctorow's article on Boingboing https://boingboing.net/2017/04/07/bug-in-tech-for-antipreppers.html
- Andre Staltz's classic article 'An Off-grid Social Network'  https://staltz.com/an-off-grid-social-network.html
- https://inthemesh.com/archive/secure-scuttlebutt-facebook-alternative/


Some work-in-progress implementations of SSB in other languages:
- Rust. https://github.com/AljoschaMeyer/secret-handshake-rs 
- Python https://github.com/pferreir/pyssb 
- Go https://github.com/andyleap/go-ssb

## Reasonable, realistic and sustainable
### We would like more information on the project's current plans for funding should this application not be succesful.

We will continue to look for funding from other sources.  We are applying to the Prototype fund and the 'mission partners' Mozilla Open Source Support award, and are considering some European Union grants.  Failing that, we are also considering a number of foundations and companies in the blockchain sector, as they have a need for such mechanisms and are investing in research and development of impactful utilities. However we would not accept funding unconditionally and have no interest in grants which would require us to significantly change our project's goals or work on proprietary software. In the meantime we will continue to maintain what we have already built.

