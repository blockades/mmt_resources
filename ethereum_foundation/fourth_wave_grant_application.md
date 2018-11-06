# Ethereum Foundation Grant: Dark Crystal

**Project Type:**
Security

**Project History**
The Magic Money Tree project started when Dan Hassan gifted 50 people cryptocurrency who otherwise would not have gotten involved in it, and used these experiences as research into what it actually takes to make cryptocurrency accessible to more diverse people. Over the last year, we have zeroed in on safe management of private keys as a foundational problem to solve. Dan Hassan then brought a team together with a track record of delivering new socio-technological open source tools and we got to work.

**Team Bios:**
Dan is a computer engineer active in autonomous co-operatives over the last decade; in areas of economics (Rootstock, Robin Hood Coop, Economic Space Agency, Enspiral), housing (Radical Routes), migration (No Borders) & labour (Footprint Workers Coop). Currently researching blockchains & data analysis for Dyne, Robin Hood Coop & University of Western Sydney Institute for Culture & Society. Caretaker of Public BigchainDB as part of the IPDB Foundation; Board Member of Robin Hood Coop.

Kieran Gibb is the CTO of Ten Thousand Things, which is combining social research and networked collaboration with software development. They experiment with community finance and support practicing data sovereignty to build software that expands the commons, producing tools that emphasise interdependency and individual autonomy.

Peg is a software engineer based in Germany, working on community based peer to peer projects over the last decade.

Mix is a programmer, teacher, and facilitator who is one of the most active contributors to Secure Scuttlebutt. He has co-founded several tech co-ops, and already fully lives the p2p crypto-powered future that he believes is the future.

Alanna is an expert in productivity and governance of distributed, non-hierarchical communities and businesses. She has significant experience building open source software to enable new kinds of organising, especially related to collaborating with money.

**Team Qualificatoin:**
Members of our team have built the world's first cooperative hedge fund (Robin Hood Coop), created open source software for collaborative organising and financial decision-making (Loomio and Cobudget), grown networks of next-paradigm social impact startups (Enspiral), participated in a 30 year long federation of cooperatives which has never had a default on a loan (Radical Routes), attracted EU funding for investigations into social currency design and community driven decision making (D-CENT and DECODE), and helped create one of the most vibrant growing ecosystems in cipherspace (Secure Scuttlebutt).

Dan Hassan has an MSc in Advanced Computing Technologies, having built a metadata search engine for the Bitcoin blockchain. Mix is a core developer of Scuttlebutt a decentralised p2p cryptographic protocol used for a range of apps from social networking to git. Alanna has co-founded a number of startups specifically in the area of open source tools for financial collaboration, and is an expert in non-hierarchical business structures. Kieran and Peg are accomplished computer programmers and community builders.

We are all experienced in effective collaboration and know how to work as a team. We are a high-EQ group, emphasising the human elements of what it takes to make great software, backed up by technical expertise. 

We also have a number of advisors and supporters: Dave Hrycyszyn (https://chainspace.io/#team), George Danezis (https://chainspace.io/#team), Dominic Tarr (https://securescuttlebutt.nz), Jutta Steiner (https://twitter.com/jutta_steiner), Elias Haase (https://www.b9lab.com/about/).

**Team Location:**
Distributed (UK, Germany, Australia, New Zealand)

**Projected Impact:**
Effective and secure key management and recovery is a "wicked problem" that has existed in the space since the advent of public private key cryptography. Everyone can use Dark Crystal for any kind of secret (a Gmail Password or location of the hidden treasure), but the need is particularly clear in the crypto ecosystem.  What we have proposed is a new composition of old tools (Shamir's Secret Sharing, Hashing, immutable logs, etc), which are also available within the Ethereum Ecosystem. We're developing a socially new approach to key management and p2p password recovery that can work with all existing crypto tools.  Scuttlebutt presents a unique petri dish within which to experiment. There are 7000 or so known users of scuttlebutt, who tend to be very experiemental and up for being test subjects. SSB has been growing consistently over the last 2-3 years and we have a lot of social capital within the ecosystem to run rapid prototyping. Not to mention, every SSB user has a built-in cryptographic secret they need to back up (their SSB identity).  Dark Crystal will be immediately useful to anyone who uses ETH. Furthermore, all of these lessons will be transferable across the Ethereum ecosystem - such as with MyCrypto Wallet or any other service where you have private keys locally.

**Proposal Summary:**
Dark Crystal is a fully p2p tool for securely backing up secrets using the trust in your social network. Your secret (wallet seed, password etc) is split into 'shards', which are given to your trusted friends. If you lose the secret or something happens to you, your friends can combine the shards to recover the secret. Dark Crystal makes this whole process simpler and less error prone, thus more accessible. Long-term, we plan to build it into a fully-featured collaborative multi-sig wallet. 

**Detailed Summary:**
The custody problem (securing private keys) is a ubiquitous wicked problem that needs solving for cryptocurrencies and cypherspace in general to go mainstream. Part of this is to do with cryptography, but arguably a larger part is a people problem. Password managers have been in use for decades, yet haven't achieved widespread adoption. Approximately 20% of all bitcoins are said to have been lost due to access errors. What we propose is a people-centric design utilising existing distributed systems. Our thesis is that this is a coordination problem rather than a purely technical problem.

There are already many tools for sharding (aka Shamir's Secret Sharing). It's a great way to enable secure recovery of secrets, making crypto a little more forgiving. However, it currently requires handling long alpha-numeric strings, which you have to copy-paste, send through various comms channels, and get people to store properly. The underlying technology has been around for decades, but no one has figured out how to make it mainstream and accessible.

We encountered this painful process ourselves when setting up multi-sig wallets. If you want each person to shard their seed, there are a huge number of string involved, and many actions that must be completed perfectly. You have to make sure everyone knows which version of what sharding tool was used, to access it again later for recombining. As a team dogfooding on ourselves (we get paid in crypto and manage wallets together), we identified the sharding process as particularly ripe for automation.

To solve these pain points, we are building Dark Crystal, named after the 80s film where they have to recombine the crystal shards to save the world. Built on top of the Secure Scuttlebutt (SSB) protocol, Dark Crystal will be fully p2p, not relying on a centralised application. All the long alpha-numeric keys will be handled in the background, making the whole process a lot simpler for the end user.

Our larger vision is to make tools for collaboratively managing cryptocurrency. Much development in the crypto space has come from an individualist mindset. Our backgrounds and passions are in cooperatives, communities, and high-trust networks, and we think crypto can become even more revolutionary by powering groups of people working together. Today, sharding is often used by individuals to increase their security, but we think it can also be used to build and share trust. Ultimately, we want to build a next-gen multi-sig wallet with built-in sharding capabilities, as we find current wallets sorely lacking in the features collaborative groups need.


**Timeline Estimate and Milestones (3, 6, 12 months):**
3 months: working prototype v1 under testing, secret recovery by initiator use case (recombining secret shards from friends)
6 months: working prototype for use case of initiator incapacitated (friends recovering your secret without your involvement)
12: really refined tool that's user and community tested, in use in other ecosystems

**PoC?**
Yes. Secure Scuttlebutt is a vibrant community full of innovators in crypto-social systems and tools. By building on SSB, we've been able to get to a usable prototype very quickly, and we have a built-in community of testers and supporters. All of the underlying plumbing is done, and we are building on top of existing cryptographically functional tooling and protocols. Much of the work will be directly transferable across most blockchain communities.

**Open Source? Which Parts?**
Yes, completely open source. The underlying SSB protocol is as well.

**How would you measure project success?**
More different people can have a good experience with crypto because they can practice secure key management with accomodations for human error and unexpected circumstances. We will feel successful if we release good working software that relieves real pain points for real people.

**Applied before?**
no

**Applied to other sources of funding?**
We have already got investment of about $200,000 USD from the personal funds of the project founder, Dan Hassan. We need another $100,000 to get the project where we think it nees to go in stage 1.

**How can the EF best support your endeavor?**
We are requesting funding so the Magic Money Tree team can keep working on Dark Crystal. Once we have the tool ready to release, we would appreciate help getting the word out, since it will be a useful utility for everyone in the Ethereum ecosystem.

**Requested Grant Amount:**
100000

**Funding Allocation:**
Our main expense is paying for our team members' time. We have some relatively small expenses related to travel, giving conference talks, research, etc.

**Total Project Budget:**
300000

**References:**
Dominic Tarr (Secure Scuttlebutt), Vinay Gupta (Mattereum, Release Manager for Ethereum), Elias Hasse (B9 Labs), Jaromil (Dyne.org), Joshua Vial (founder of Enspiral)
