
## Some applications and implementations of shamirs secret sharing

* [Life, Death, and Splitting Secrets](http://www.moserware.com/2011/11/life-death-and-splitting-secrets.html) is quite an interesting article from someone who decided to write a secret sharing program after dealing with the death of their grandmother and executing her will.  The software itself is nothing special, other than that for bigger secrets it integrates GPG file encryption with key splitting.
* [DNSSEC](https://www.schneier.com/blog/archives/2010/07/dnssec_root_key.html) Alledgedly the root key for ICANN DNS security is held by 7 parties, based in Britain, the U.S., Burkina Faso, Trinidad and Tobago, Canada, China, and the Czech Republic.  Many people assume that they are holders of 5-of-7 shamir's shares.
* [Homomorphic secret sharing](https://en.wikipedia.org/wiki/Homomorphic_secret_sharing) This wikipedia article describes an electronic voting system where each vote is sharded and sent to a number of different vote-counters.  A single vote counter is unable to manipulate votes in a directed way.  Corruption can only occur when **all** vote counters maliciously collaborate.  It is based on a paper from Berry Schönmakers (1999).
* [PolyPasswordHasher](https://polypasswordhasher.github.io/PolyPasswordHasher/) uses shamirs secret sharing to build a password database which claims to be considerably more difficult to crack passwords if the database is compromised compared to traditional methods.
* [GPG revocation certificates](https://www.hackdiary.com/2004/01/18/revoking-a-gpg-key/).  Suppose an activist was captured by authorities and their computer impounded.  They might want their friends to revoke their GPG key, so that people know to stop sending them sensitive information.  If they had sharded their revocation certificate and sent shards to their friends, this would be possible. 
* [threshcrypt](https://github.com/ryancdotorg/threshcrypt) an interesting implementation of file encryption using shamir's secret sharing.  It takes things a step further, adding passwords to each shard.
* [ThresholdJS](https://github.com/karlgluck/ThresholdJS) a minimalist implementation designed specifically for bitcoin private keys. [live demo](http://karlgluck.github.io/ThresholdJS/)
* [Vault by HashiCorp](https://www.vaultproject.io/) made by the same company as 'vagrant', vault is a secret management tool which uses, among other things, shamirs secret sharing. 
* [PassGuardian](http://passguardian.com/) - a web based implementation of sss using the original secrets.js (of which #dark-crystal uses a fork).
* and not to forget [secrets.dyne.org](https://secrets.dyne.org/) and of course [truename](https://github.com/KGibb8/truename-index)


 
