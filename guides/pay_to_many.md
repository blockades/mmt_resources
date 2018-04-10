
# Using Electrum's 'Pay to many'

When paying wages, or any other situation where you might want to pay more than one person, a useful feature of Bitcoin which is 'batch payments' or 'pay to many' as its called in Electrum.

Bitcoin transactions are composed of 'inputs' of the coins being spent and 'outputs' of where they are going to.  Its possible for a single transaction to have many outputs going to different addresses.  Which is handy because it saves fees, reduces 'traffic' on the network, and, in the case of a multi-signature transaction, means less transactions to sign. 

- In electrum go to 'Tools' > 'Pay to many'
- It brings up a little info box telling us to give a list of addresses and amounts separated by a comma, eg: address, amount
- It then brings us to the 'Send' tab, just like for making a normal payment, but the 'Pay to' box is bigger so we can enter a list into it instead of a single address.  The list might look something like this:
```
bc1lsdkfjdslfkjsdflkjsdlf, 0.15453245
bc1lsrewfrwlfkdsfffj34jds, 0.46453245
bc1dfjflkjslfkjsdf345gsdf, 0.53245543

```
- From this point on you do everything the same as though it were a single payment. 

It is also possible to read the list from a file, which you can do by clicking on the picture of a folder in the bottom right corner of the 'Pay to' box.


