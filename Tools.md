# Tools / Tool resources

## wallets

* [Electrum Bitcoin Wallet](https://electrum.org/#home) - [Cold Storage — Electrum 2.10 documentation](http://docs.electrum.org/en/latest/coldstorage.html#create-a-watching-only-version-of-your-wallet) 
* [MyEtherWallet.com](https://www.myetherwallet.com/) - javascript based Ethereum wallet.
* [NEON](http://neonwallet.com/) - NEO wallet
* [MyZenWallet.io](https://myzenwallet.io/) - Zencash wallet.

## privacy/ security tools

* [Diceware Secure Passphrase and Password Generator](https://www.rempe.us/diceware/#eff)
* [KeePass Password Safe](https://keepass.info/) - Software for managing passwords
* [dyne/Tomb: the Crypto Undertaker](https://github.com/dyne/Tomb) - [Tomb :: File Encryption on GNU/Linux](https://www.dyne.org/software/tomb/)
* [dans tomb guide on scuttlebutt](https://viewer.scuttlebot.io/%25S9KShHdAxUKhhLQxVf9R8fVcU4RdzfJZ06w8fmRLkOE%3D.sha256)
* [CryptoParty handbook](https://www.cryptoparty.in/learn/handbook)

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


