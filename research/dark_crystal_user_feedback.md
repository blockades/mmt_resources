# Dark Crystal user testing feedback report

- TODO image
- TODO: should we remove names of users?

## Introduction

We filmed a series of testing sessions, and also asked for feedback from the community in the #dark-crystal-feedback channel

## Issues raised

## Difficulty with 'mentions' when choosing recipients for a secret



### Piet

> On the main page of DC, I clicked on the image of the person who had sent me a shard.
> I expected to it to take me to the details of the shard.
> Instead it took me to their profile.

### Alanna

> Just used Dark Crystal to shard my first 'real' secrets. A couple pieces of user feedback....

> The name and label sections are confusing. I would assume that both fields would be visible to myself and the people I'm sending the shards too. If it's otherwise, I need some guidance text or something letting be know.
> I find it disconcerting that the shards I have for other people's crystals don't have names. Like if someone sent me a shard and then called me up to confirm if it came though, I would have no way of differentiating if I already had other crystals from them. Maybe when you mouse over that shard, the name should show up? Same if you click into the list of someone's shards.
> Instead of 'perform ritual' it should probably be 'shard crystal' or 'send shards', because that's the action you're taking.
> Overall, it was really smooth! Soooo much better than last time I did a round fo sharding using the old manual process shudder.

### Grace

Test case wished to remain anonymous, so I will refer to them as Grace.

### Approach:
* Given minimal prior information
* Attempt to simulate a new user arriving after installing from our website
* 3 computers setup on same LAN
* @kieran & @kieran-two were on-hand to return shards
* _tried_ to have users sync'ed and up to date _before_ we started the test, but that was hard!
* Video'ed (for personal reflection)

### Prior information:
* A nearly new scuttlebutt user, had installed Patchwork over the weekend but hadn't really used it at all, just had let it replicate for a while.
* Grace was not a tech nerd, but tech-savvy as a regular internet-generation kiddie

### Grace was given the following instructions:
1. Download and install Patchbay
* Go to https://github.com/ssbc/patchbay/releases
* Find the latest release, donwload and install

2. Open Patchbay
* Click on the circle icon in the top-right corner and click on the menu option `/dark-crystal`

3. Visit DarkCrystal website
* Nagivate to https://darkcrystal.pw
* Read the description of the application on the landing page

4. Your Mission!
* Share a secret with @kieran and @kieran-two
* Recover the secret you shared

* (additional step we half-played with) return a shard belonging to @kieran

### Live Observations
We had many non-UI related issues which meant that we were unable to dive too deep into discussing design.

* If Patchbay hasn't indexed / loaded fully, you can't find custodians (suggestify doesn't work properly, all the names don't appear). :-1: 
* The exact case was Grace tried to create a new secret and 
* @kieran wouldn't appear, only two people did were full public keys @ABCD1234... (and they weren't the right people either).
* Grace did not assume they were the same person, but actually typed in @kieran @kieran-two and tried to see if it worked.
* Errors were thrown, but the error wasn't particularly helpful / descriptive enough of how to help deal with the problem.
* After minor intervention to explain what was going wrong, Grace then assumed the two identities were the correct people. Only after further intervention to correct her and ask her to restart the app (and wait 20 minutes) were we able to continue.

* When creating a secret, Grace first tried to select 3 instead of 2 quorum. This was a test to see if it would break, rather than actually making a wrong decision

* Sharing a secret was obvious :+1: 

* SSB has major onboarding problems! People expect apps to _just work_ / people are impatient :-1: 

* Shard never arrived with @kieran-two :man_shrugging: so Grace was unable to retreive the secret :-1: 

* Patchbay problem - indexes constantly reset? Friends never load or are missing some people.\ :-1: 

* Configuration / setup issues
* make sure everyone is connected and following eachother in advance

* Shard sent to Grace by @kieran in 3rd part of mission never arrived! :-1: 

* Grace observed if you have more than a certain number of secrets, how are you going to remember which one is which?! And how are you going to filter / find the correct one?

### Summary
* Had to wait at least 20 minutes for Patchbay to index which was disruptive
* Shards didn't gossip properly, or weren't rendering.
* Sharing a new secret was obvious
* Custodian suggester input field should really show everyone you're connected to immediately, shouldn't show only half the number of people, etc.
* Better view for list of secrets required
* Does naming a secret work? Will you remember? Does that require a 'long-term' user test? e.g. get someone to attempt to recover one of a number of secrets they shared 3 months after they shared it.

### Personal reflections
* Nothing too new, I already knew about SSB onboarding issues!
* Feels difficult having to lower people's expectations when starting the app, 'and now we've gotta wait for a while...'
* Feels difficult doing it in Patchbay as its an extra step which feels unnecessary / unwanted
* Ongoing challenge of uncertainty of replication / managing people's expectations for immediate data sharing - sometimes the data doesn't arrive in time or at all. Sometimes it arrives perfectly. Never knowing whether its going to work or not is frustrating and stressful.
* `/network` feature wasn't available as part of the latest release, only in git master branch, so was unable to use that new feature to streamline the process of getting Grace connected to @kieran and @kieran-two.

### Lessons for Next Run!
* Will try with **absolute bare minimum**, get someone to use a blank identity on my computer, unconnected, and see what happens. Screen out SSB on-boarding troubles to get clear interaction with just Dark Crystal
* Won't use Patchbay, will use Dark Crystal standalone installer.
* Get someone to navigate my existing interface (with loads of dummy shards) and see if they can work out how to move around that.

## Greg Kan

- https://www.youtube.com/watch?v=0bWeN9st2Sw

Wow we found a lot of bugs and confusing things in such a short time! Probably the best use of 10 minutes I can imagine. I knew some stuff was un-ideal, but I saw so so much more through Greg's eyes, thank you thank you thank you :heartpulse:


**Who**: [@gregkan](@0hZ8ZEIxhzVBjGWodx1piF3oRLBQ3cMSv1u7dkCJ9ao=.ed25519) is a programmer, [po](https://www.goodreads.com/book/show/28592625-this-paper-boat)[et](https://www.radionz.co.nz/news/the-wireless/373951/poetry-from-a-seance-gregory-kan-on-his-collection-this-paper-boat), and part-time philosopher. He'd heard a little about DarkCrystal, but not used it before.

**Where**: this is a short (7:42) hallway test in the actual hallway outside Dev Academy.

**Summary:**
- found making shards easy
  - knowing what the "secret" field was needs more clarification
- **navigation** was confusing
  - how do I get back to the main page
  - if I click the header (Dark Crystal) does it take me to the main page
  - expects `Backspace` to take him back from a profile to Dark Crystal
- looking at a secret:
  - able to interpret the history, the quorum etc fine
  - wasn't obvious how to show secret
- **others shards** vs **others crystals** was confusing
- Others Shards page
  - knew what blinking meant (there was a request)
  - didn't know what the others were (there was no helping text)
  - page was waaay too long for some reason
  - **Forwarding**
    - was able to fwd
    - didn't know what consent meant here
    - was able to select forwarding from `Kieran2 > Kieran2`
- Others Crystals page
  - don't think he understood what it was in comparison to others shards  

## Abdulla

- http://ameba.ehion.com/download/usertest1_part1.mp4
- http://ameba.ehion.com/download/usertest1_part2.mp4

I tried to film it but the video is terrible, mostly due to my daughter interfering but also my friend wasn't super comfortable with having the camera on and (as is often the case) gave me much more in-depth and useful feedback once i'd turned the camera off.

But the overall result was: he found it pretty difficult to make much sense of the interface.

I had only explained that it was a tool for backing up secrets or keys by sending several pieces to trusted friends, and that it was built on a peer-to-peer network. And he was dumped in front of my account with some existing secrets with had little context to him so perhaps this test is a bit unfair.

Knowing only this, he did manage to share a secret, but he was not sure what the quorum was, was confused by the word 'custodian', and didn't understand what the 'request' button would do. Although he had never used Dark Crystal or Scuttlebutt, he is a software developer with experience in web development and front end design.

Another problem was that he was using my account and fired off some shards to some random people. (oh dear!)

He said the language used was unintuitive and suggested that we use 'tooltips', more explanatory messages, and provide online documentation.

He also said the pink was too bright (but i love it!).

## Antje

- http://ameba.ehion.com/download/usertest2.mp4

## Cel (not sure if this should go here)

> Possible good use case for #dark-crystal : 2FA backup codes. You know the list of single-use codes that some web services give you so you can log into your account if you don't have your phone/2FA/TOTP device.



### Bit_Tron

Ali observed the 'secret' field suggested some kind of extra cypher input to doubly secure the SSB private key!

Secret too big!

quorum of 1 still triggers cascading errors (mac)

when filling in custodians with the dropdown ESC  could mean exit the dropdown, not the form modal!

### lachenmayer

metaphors confusing
- shards and crystals is confusing!
- could have some explanation text
- name vs label
    - title vs description?
    - overlapping concepts
    - labels could imply tags
- better description of the fields!!
    - whats public / whats private?
    - label confusing! why not just include it in the secret?
    - multiple secrets?
- quorum as a slider, min 2!
- custodians vs quorum - visualise using a trust indicator as a 'progress bar' / password strength indicator


- now ive shared the secret, and have a crystal in my interface, where has it gone?
    - offline - has it actually sent yet - synced to the broader network yet?
    - 'shard sent' - what does that mean? Has it _actually sent_ or is it just published locally
    - useful to say 'published locally - waiting to sync' and then 'shard sent'
    - shard never arrives?
    - secret now shared with these people - you can't now read this.

- magical language is confusing - is obfuscating?
    - cliquey / subtle barrier
    - crystal meth????
    - cultural barrier with the language used
    - metaphors used
    - ideation stage was relevant - scalability possibly a barrier?

- main view - YOU HAVE A SHARD! Push notification that says 'CONTACT THIS PERSON'

- message thats acknowledge - need to know when and where it lands!

