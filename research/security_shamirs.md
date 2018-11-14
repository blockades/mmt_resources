
*** this article is a work-in-progress and probably doesnt make sense yet ***

## Security considerations for Shamir's secret sharing

A bit of an update from Dark-Crystal. We are continuing to develop the identity recovery system. Parallel to this we are currently researching two areas.  Adopting secp256k1 keys, and security issues/vulnerabilities with Shamir's secret sharing and how to approach them.  This article is about the latter, and we hope that this will be useful for other projects considering using Shamir's scheme.

In general, Shamir's scheme is considered information-theoretically secure.  That is, individual shares contain absolutely no semantic information about the secret, making it 'post quantum' crytography.

An interesting anecdote, the root key for ICANN DNS security, effectively the key which secures the naming system of the internet, is held by seven parties, based in Britain, the U.S., Burkina Faso, Trinidad and Tobago, Canada, China, and the Czech Republic. Cryptographer Bruce Schneier has alleged that they are holders of Shamir's secret shares.

However, we have identified several issues with it. 

### The need for verification of individual shares

Harn and Lin consider the situation in which 'cheaters' claiming to be holders of shares introduce 'fake' shares, causing the incorrect secret to be recovered. 

We also considered the possibility of genuine holders of shares might have a motivation for not wanting the secret to be recovered, and could maliciously modify their share.  Furthermore, the share might be modified by some accidental or external cause.

It might be very easy to determine that we have recovered the wrong secret.  Either because we have some idea of how we expect it to look, or as we have recently implemented in dark crystal, an identifier is added to the secret to allow the correct secret to be automatically recognised.  (We concatonated the secret with the last 16 bytes of its SHA256 hash). 

However problem here, is that although we might know for sure that we have not successfully restored our secret, we have no way of telling which share(s) have caused the problem, meaning we do not know who is responsible. 

The solution is to introduce some verification of shares, and a number of different methods of doing this have been proposed.  Generally they rely on publicly publishing some information to allow anybody to verify a given share, a zero-knowledge proof.

#### Publicly publishing the encrypted shares  

This is what we were originally planning to do, but this only helps in this context if the encryption scheme used is deterministic.  That is to say encrypting the same message with the same key twice will reliably give the same output.  The problem here is that such encryption schemes are vulnerable to replay attacks.  Most modern asymmetric schemes introduce some random nonce to evade this problem. The scheme we are using (libsodium's secret box) typically takes a 24 byte random nonce.  So this is not a good option.  However we actually already 'wrap' shares in a second level of encryption to to allow the secret owner to publish their own encrypted copy of the shard message with its associated metadata as a way to keep a personal record of what was sent to who. When we looked at other schemes for verifiable secret sharing we found they involved a similar practice, and we decided to use an existing well-documented scheme. 

#### Publicly publishing the hash of each share

This is also something we considered, but feel that it gives custodians more unnecessary extra information and less accountability compared to other methods.

#### Feldman's scheme 

#### Schoenmakers scheme

#### Implementations

- https://github.com/songgeng87/PubliclyVerifiableSecretSharing - C implementation built on secp256k1 used by EOS
- https://github.com/FabioTacke/PubliclyVerifiableSecretSharing - A Swift implementation 
- https://github.com/dfinity/vss - Dfinity's NodeJS implentation built on BLS, and used for their distributed key generation


### Share size has a linear relationship to secret size

Anyone holding a share is able to determine the length of the secret.  Particular kind of cryptographic keys have a characteristic length.  So the scheme gives away more information to custodians than is necessary.  Our solution to this is to add padding to the secret to increase share length to a standard amount.

### Revoking shares if trust in a custodian is lost

Suppose we loose trust in one person holding a shard. This might be because they had their computer stolen. Or maybe we had a really bad argument with them. Or maybe we found out they weren't the person they were claiming to be.

In Shamir's original paper he states that one of the great advantages of the scheme is that it is possible to create as many distinct sets of shards as you like without needing to modify the secret. Each set of shards is incompatible with the other sets. Using Glenn Rempe's implementation, if we run the share method several times with the same secret, we get each time a different set of shards. When generating a new set, an extra check could be done to rule out the extremely improbable case that an identical set had been generated.

This means in a conventional (shards written on pieces of paper) secret sharing scenario, we could simply give new shards to the custodians we do still trust and ask them to destroy the old ones. This would make the shard belonging to the untrusted person become useless.

In our case, we are using the Secure-Scuttlebutt's immutable log, we have no way of destroying a message. 

Something like this:

Alice sends a request to Bob, "hi Bob, can you look after a secret share for me?"
Bob replies "yes, encrypt it to this ephemeral public key bob_e". Bob's stores this key on disk, for now.
Alice also generates an ephemeral key, alice_e and encrypts the share, sending bob alice_e.public, secretbox(share_bob, alice_e*bob_e) then deletes alice_e's private key. (note: alice sends the public key she used to bob, he'll need that to decrypt the share)

Later, she wants to update the share - she sends a message to bob: "please delete that share" and bob deletes his ephemeral key. Now bob can't decrypt that share anymore! So if an attacker gets a hold of bob's device, they won't have that share either.

If bob sent an array of ephemeral keys, then alice could update the share that many times without having to do another round trip.

PS. you'd better also look into how to securely delete files. I think this might depend on the underlying storage architecture sometimes. Or it might be as easy as just writing 0's over the file.

### Secure computation

having a dedicated virtual machine for secure computation. But my feeling is that as long as the secret is initially stored on disk, we are not really adding anything by having an ultra secure system of generating shares.

### Conclusion

We feel confident that we are able to address the issues we have explored in this article.  However we have focussed here mainly on technical limitations of the scheme.  There are many other social aspects which pose problems to our model, which we will explore in another article. 

## References (needs sorting out)

- https://crypto.stackexchange.com/questions/10904/post-quantum-threshold-secret-sharing
- shatter secrets
- Harn, L. & Lin, C. Detection and identification of cheaters in (t, n) secret sharing scheme, Des. Codes Cryptogr. (2009) 52: 15. [link](https://link.springer.com/article/10.1007/s10623-008-9265-8)
- how not to share a secret

- Shamir, Adi (1979). "How to share a secret". Communications of the ACM. 22 (11): 612–613. doi:10.1145/359168.359176.
- Blakley, G.R. (1979). "Safeguarding Cryptographic Keys". Managing Requirements Knowledge, International Workshop on (AFIPS). 48: 313–317. doi:10.1109-/AFIPS.1979.98.
- Beimel, Amos (2011). "Secret-Sharing Schemes: A Survey" http://www.cs.bgu.ac.il/~beimel/Papers/Survey.pdf
- Schneier, Bruce (2010) - DNSSEC Root Key held by 7 parties worldwide https://www.schneier.com/blog/archives/2010/07/dnssec_root_key.html
- Feldman
- Schoenmakers, Berry (1999) "A Simple Publicly Verifiable Secret Sharing Scheme and its Application to Electronic Voting" Advances in Cryptology-CRYPTO'99, volume 1666 of Lecture Notes in Computer Science, pages 148-164, Berlin, 1999. Springer-Verlag. 
- https://zenroom.dyne.org/


