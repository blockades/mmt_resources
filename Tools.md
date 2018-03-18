# Tools / Tool resources

## wallets

* [Electrum Bitcoin Wallet](https://electrum.org/#home) - [Cold Storage — Electrum 2.10 documentation](http://docs.electrum.org/en/latest/coldstorage.html#create-a-watching-only-version-of-your-wallet) - Actively developed open source bitcoin wallet.
* [Samourai Bitcoin Wallet](https://samouraiwallet.com/) - Open source mobile bitcoin wallet with good security features. 
* [MyEtherWallet.com](https://www.myetherwallet.com/) - javascript based Ethereum wallet.
* [MyCrypto.com](https://mycrypto.com/) - javascript based Ethereum wallet (fork of MyEtherWallet - most of the original devs).
* [NEON](http://neonwallet.com/) - NEO wallet
* [MyZenWallet.io](https://myzenwallet.io/) - Zencash wallet.

## blockchain explorers and statistics tools

These are websites which allow you to get information about addresses and transactions on the blockchain without needing a host your own node. 

### Bitcoin

* [oxt.me](https://oxt.me) - bitcoin explorer for both types of bitcoin address (bech32 and standard)
* [blockchain.info](https://blockchain.info) - bitcoin explorer for standard bitcoin addresses only
* [Johoe's Bitcoin Mempool statistics](https://jochen-hoenicke.de/queue/) online tool which allows you to see unconfirmed bitcoin transactions and current fees.  Useful for determining 'quiet times' for making cheaper/faster transactions or when manually choosing fees.   
* [Statoshi.info](http://statoshi.info/) bitcoin node statistics software developed by Jameson Lopp.

### Ethereum

* [etherchain.org - Ethereum Blockchain Explorer](https://www.etherchain.org/)
* [ethstats.net](https://ethstats.net/) ethereum live statistics. 

### Neo

* [neotracker.io](https://neotracker.io/)

## privacy/ security tools

### Password management
* [KeePassXC Password Safe](https://keepassxc.org/download/) - Well-established multi-platform software for managing passwords
* [Diceware Secure Passphrase and Password Generator](https://www.rempe.us/diceware/#eff) - online password generator
* [Pass: The Standard Unix Password Manager](https://www.passwordstore.org/) barebones simple command line password manager using [gpg](https://gnupg.org/) with optional [tomb integration](https://github.com/roddhjav/pass-tomb#readme)

### Encryption
* [GNU Privacy guard](https://gnupg.org/) - encryption tool for files and email.  Can be integrated into most email clients.  
* [dyne/Tomb: the Crypto Undertaker](https://www.dyne.org/software/tomb/) file encryption software with some great features. [tomb on github](https://github.com/dyne/Tomb) - [dans tomb guide on scuttlebutt](https://viewer.scuttlebot.io/%25S9KShHdAxUKhhLQxVf9R8fVcU4RdzfJZ06w8fmRLkOE%3D.sha256)
* [CryptoParty handbook](https://www.cryptoparty.in/learn/handbook) - guide to hosting an event to help each other setup encryption software and share public keys. 

## Backing up keys to paper

It is possible to create and print a QR code of a [secrets shard](https://secrets.dyne.org/), any kind of key, or other important data.  You can then think of an ingenious physical hiding place...

* [qrencode](https://fukuchi.org/works/qrencode/index.html.en) Command line tool and library with bindings for several programming languages to generate QR codes.  Simple usage:  `cat keyfile | qrencode -o key.png`.  Available in most linux distribution repos. 
* [QR Code Generator](https://www.qr-code-generator.com/) Online service to generate QR codes.  Trustworthyness unknown... 
* [PaperBack](http://ollydbg.de/Paperbak/#1) A bit more old-school, a program that allows you to print data to paper designed to be restored by a scanner.  500kb can fit on an A4 page. 

### Paper wallets

Bitcoin wallets can be generated and printed with QR codes for the public and private keys.  For security reasons is recommended to only use them for a single transaction, for example, to give as a gift, and when the reciever gets the gift they transfer it to another address. 

* [Paper wallet article on Bitcoin Wiki](https://en.bitcoin.it/wiki/Paper_wallet)
* [Bitcoin address utility](https://github.com/casascius/Bitcoin-Address-Utility/) is a program which allows you to create such paper wallets.
* There are also several websites which offer to generate paper wallets.  Trustworthyness unknown...


## collaboration tools

* [HackMD - Collaborative markdown notes](https://hackmd.io/)
* [Github tutorial](https://try.github.io/levels/1/challenges/1)

### Terminal sharing

[GNU Screen](https://www.gnu.org/software/screen/) is a terminal multiplexer which, among other things, allow multiple users to share the same terminal which can be useful for demonstrating things or helping each other with problems.  See this [multiuser screen documentation](http://aperiodic.net/screen/multiuser).  You can also do this with [tmux](https://github.com/tmux/tmux/wiki).

This can be combined with reverse ssh tunnelling (which sounds more complicated than it is) from some common remote server to allow people to access a local machine without worrying about setting up user accounts, forwarding ports, and not having a static IP address.  

So imagine i cannot manage to install our latest software project on my local computer and i want help from someone, but i want them to do it in a way that i see what is going on.  If we all have ssh access to a common remote server, I can create a reverse ssh tunnel to it like this: 

`localcomputer$ ssh -R 2000:localhost:22 user@remoteserver`

This will connect to the server as normal, but also open a tunnel so that I can connect back on port 2000 (any port over 1024 should work). 
I can then initiate a named screen session for other users to connect to with 

`screen -d -m -S multisession`

and connect to it myself with:

- `screen -r multisession`
- then do `Ctrl-A :multisession on`
- then do `Ctrl-A :acladd username` for each additional user (these commands can be added to `.screenrc` to save typing them every time)
- `aclchg` can be used instead of `acladd` to use specific permissions eg: readonly (they can see the screen but not type commands)
- Then invite other users to connect with `screen -x username/multiuser` where `username` is the user who initiated the screen session to connect to.
- Then ssh back to localhost effectively taking connected users along... `ssh -p2000 localuser@localhost`
- Another handy tool, [ngrok](https://ngrok.com) can be used to expose a website served on localhost by doing `ngrok http 80` ([see documentation](https://ngrok.com/docs)).  ngrok could also be used as the remote server to expose ssh (`ngrok tcp 22`) but this requires signing up for an ngrok account. 
- Combined with mumble this could be a nice way to fix stuff interactively or demonstrate how to do something

## ruby programming 

* Ruby programming: [ruby koans](https://github.com/CUNY-TAP/ruby-koans)
* [Basic Ruby app with Sinatra](https://github.com/wegotcoders/wgc_groundwork)
* [bbatsov/ruby-style-guide: A community-driven Ruby coding style guide](https://github.com/bbatsov/ruby-style-guide)


## containers

* [docker 'from scratch'](https://embano1.github.io/post/scratch/)
* [50+ Useful Docker Tools | Caylent](http://caylent.com/50-useful-docker-tools/)
* [Dockerizing a Ruby on Rails Application - Semaphore](https://semaphoreci.com/community/tutorials/dockerizing-a-ruby-on-rails-application)
* [Quickstart: Compose and Rails | Docker Documentation](https://docs.docker.com/compose/rails/)
* [Rancher](http://rancher.com/) open source container management platform
* [Travis CI](https://travis-ci.org/)
* [captainduckduck: Automated Scalable Ready Webserver Package | In experimental phase](https://github.com/githubsaturn/captainduckduck/)

## tech reading/ resources

* [Open Source Guides | Learn how to launch and grow your project.](https://opensource.guide/)
* Many different programming languages: [code academy](https://www.codecademy.com/)
* Maths problems: [projecteuler.net](https://projecteuler.net/)
* [OverTheWire: Bandit](http://overthewire.org/wargames/bandit/) game to help improve command line skills
* [webpro/awesome-newsletters: The best (weekly) newsletters](https://github.com/webpro/awesome-newsletters)


## unsorted

* [Triple Entry Accounting](http://iang.org/papers/triple_entry.html) - Ian Grigg
* [EOS - an Introduction](http://iang.org/papers/EOS_An_Introduction.pdf) - Ian Grigg
* [ssbc/patchwork: A decentralized messaging and sharing app built on top of Secure Scuttlebutt (SSB).](https://github.com/ssbc/patchwork)
* [Blockstream/satellite: Blockstream Satellite](https://github.com/Blockstream/satellite)


