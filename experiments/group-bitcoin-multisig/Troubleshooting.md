# Bitcoin Multisignature Experiment

## Troubleshooting

### 1. Transparency

* Concerns over lack of transparency inbuilt into the multisignature wallet
* Bitcoin multisig capacity largely designed as a security protocol for an _individual_, not necessarily thought about in terms of a group, or at the very least a horizontal / non-hierarchical group.
* Who the cosigners of a transaction are is never visible on the Blockchain or internally in Electrum.
* Why the transaction is approved, or a description of the transaction/payment is never shared via the Blockchain or Electrum
* Who the payee is only visible as a BTC address. For the sake of the group it would make sense that each could see who the destination address belonged to, or a note could be left by the cosigners and is shared with all possible cosigners (not public).
  - Electrum contacts can be added, this could resolve issue for each person individually. Does not resolve for group until each person has the addresses of all other cosigners.
* Opens up space for group disputes. A bad actor could exploit this lack of accountability and create distrust and disputes.
* In a way, its a positive that this information is _not_ recorded on-blockchain as the tx information and/or cosigner's identities should not be public information.
* Negative in that this information _could_ be encrypted so that only wallet cosigners with access to the wallet could view this information. Or it could be shared via some kind of centralised point (such as a server)
* **Opens up a space for the design of either a direct integration or a module that provides integration functionality between a multisignature wallet and a transparency tool such as CoBudget or OpenCollective.**

### 2. Late Night Accounting

* Mistake made while approving a late night and slightly rushed transaction at the end of a phonecall and sending more bitcoin than indended (by factor of 10)

