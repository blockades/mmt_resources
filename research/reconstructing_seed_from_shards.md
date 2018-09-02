
# Reconstructing seeds from shards

@Alanna did the shard combining during our last meeting.  Lots of issues came up.  Which is a good thing!
  
- There is a lot of confusion created around that multisig wallets having different amounts of required signatories (eg: 4 of 5) and sharding keys can have different amount of required shards to reconstruct (eg: 3 of 5).  
- We could each choose the amounts of required shards when sharding our seeds.  Which also lead to a bit of confusion.  Although maybe the confusion was more about a star trek joke!?  Dyne.org's implementation of secret sharing gets around this by forcing us to use a fixed number of shards (3 of 5 i think).  This keeps things simple, but comes at the cost of the flexibility of the tool. 
- Imagine being in alanna's position of being given a load of shards from different people and for different people's keys and trying to keep track of them all.  Confusing. 
- @mix also mentioned there could also be confusion about which implementation of secret sharing people used (was it truename or dyne?). 
  
Despite all this, alanna recovered dans seed pretty quickly.  A good thing is that its pretty easy to tell when its done right - you suddenly see a bunch of english words instead of random characters.  But this might have not been so obvious if we were sharing a key which looked random instead of a seed. 

We now have dans seed, but this is not the end.... our adventures in getting back our 50c are [continued in this thread](%oQK5s8LRRwFLC3FMS/xRI5b7yLlz2i0VjWXZK0VN1jo=.sha256) with wonderful pictures 
