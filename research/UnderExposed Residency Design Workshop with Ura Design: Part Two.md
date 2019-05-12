# UnderExposed Residency Design Workshop with Ura Design: Part Two

tags: #darkcrystal #design #simplysecure   

ssb cypherlink: %qtEIi+IfbwN0s9fM8SfLNp4eW8VuTnp7mDzwS84JBr0=.sha256

![](https://i.imgur.com/XuO7yAm.jpg)

[UnderExposed Residency Design Workshop with Ura Design: Part One](https://hackmd.io/s/rJ1dtYB2N)

## What Happened Next?

After running through the application with the summary and initial gut reaction the next process was to put pen to paper and to recreate the existing interface elements as pieces of paper which we could then speak about and move around.

The first page we did was the /dark-crystal (homepage). 

![](https://i.imgur.com/ambgkeX.jpg)

Laying out each element on paper highlighted that it was not clear that each Crystal was made up of Custodians and a Quorum. We then added some avatars to represent Custodians, the Quorum and then also saw we could highlight which state the Crystal was in by marking which Custodians (if any) had returned shards and if Quorum had been met (by using a blue tick). 

It was during this process that Elio asked if there was any other logical primitive involved in Crystals other than Shards and Holders of Shards. In other words are Shards the primary building blocks?

We tested this question out by looking at my perspectives of Shards as they might appear within the application:

- I may hold shards which others have asked me to keep hold of (I am a Custodian).
- I may hold shards forwarded to me by other people (I may have lost my old computer, have set up a new account and have asked the Custodians of those shards to forward them to my new account).
- I may hold shards which have been returned to me by other people. 

We also clarified that shards can relate to each other by being part of the same crystal.


In all these cases we are just dealing with Shards. Elio wanted to try and organise all of these 'types' of shards into one view to see what would happen. He used the analogy of an Inbox (and given that [Ura were redesigning parts of the Thunderbird email client](https://www.opentech.fund/news/december-2018-monthly-report/) at the time they likely had inboxes on the mind ;) )


![](https://i.imgur.com/Wm7BJbK.jpg)


First notes are that this was 30 mins of mocking up. Now I'll run through each of the rows. Each row resembles a different 'type' of shard. I, Dan Hassan, am the owner of this inbox, so it's from my perspective.

- The first row is an entry for a shard I am holding as a Custodian for Alice. We can see that I have returned to the Author.
- The second row is an entry for a shard which has been returned to me by Alice.
- The third row is a shard I am holding of Bob the Builder which I have forwarded to Bob Senior. The use case here is that Bob the Builder died so we have forwarded the shards to Bob Senior as Bob the Builder asked me to do in this scenario.
- The fourth row is shard which has been forwarded to me by Alice. I lost my computer and have asked Alice to forward me my shards from the old account.

This is a first draft and far from complete but it was interesting seeing a different approach to displaying information about Shards. With this as a base we could start to explore how to group shards by Crystal Root ID so that shards belonging to the same Crystal are grouped together. 

Rethinking the view of Shards seemed like a good thread to pull to see if we could clarify the conceptual tangle of `My Crystals`. `Others Shards` and `Others Crystals`...



