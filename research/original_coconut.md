
## Using secret sharing

To give you an example of how this works, lets imagine that I am one of the multisig signers. 

I setup a wallet which generates a seed:

'lets pretend that this string of words is my seed for my wallet which is part of the multisig setup'

I would then run [secrets.dyne.org](https://github.com/PIENews/secrets) locally (in this example we'll use the online hosted version for display purposes).

So... I go to http://secrets.dyne.org/share

and I input my secret:

> lets pretend that this string of words is my seed for my wallet which is part of the multisig setup

This spits out the following encrypted shards:

> NNRFZKW477GXH36NV2NP9CRWKXVR64AM3LZPE2U2ME57GE9U3K85N5SEX749L5PFK92235PHKDRM9D42C43PM8XDLC5GG8W42QCPW762PLU9D29M9LUXGG3GKRLCWVR2QW7SN9XG5KQWUV9XGK2REC68K3L8VB7EV2KV6KH9D4K5QZZCP2LG56W2B8R8EWP2PHKR795LQDFW69D7X73AREVP647ZH6

> QLRBQ7368PNDUE7Q3RRZ4AVM7K8KQ7FP46VL32HK9GM3X9XC872VMGESQL7X9V4XH5GE42X7VCWP843Z24A37EQM36VHGQNMP267B6QXLZXKFXP2GGPQU2689P5VVU5NW7WQEAXE4264N5C9NEGXXNQUEX9KGZQT7K8MWR5QTD3WVQMD5TE2ZG4P4EC93NL9V93CZL4WG6W8S7K52GGVWHVE2RDL83UZ

> QLRBQLEVWGD8C8LLLK28PS9KWZER78FL84VG2MBK6M8VD24FDWDMZW7FENMWN6RMFGPDZZ74PUM7N4PD9WAQ2ZR7LZ5S2M6LPN7LAL29QZ36U3G5PR8WC97GZE4NLBXW3MVLXNFGPZGEXZ5AMDMGRW53T4N5VQ6VBP9W398XRULE8VR6G5HQ6MR7R9QA23DWX9KZTN8W4ZGRGBX3QPPMXXAPNE3XEE6FE

> PNRFKMV7Z82PSXRKXG7RKHG38E9852F9ZNPPV3SX9Z53M5WC8GG5XGZUVL62MD7XSNER4NEZRSZE5WRGNZTQ8PRK8PNCVKGVZ8K9T96RZXRD4TKR8LWP7AVGM4XQ8MU5LGNVLD6AW453RLG9F2LEX3MENC55QGRWGSG7N3683LBKNR252QZBNE9872XECQM4K3GQEC797W5LENCL7G85VXDC3D4E29NRT7

> G3ZUQE3WW4R9CE6GL9WQMF86RDK5M8TZ42K7GKBP9QMQ3Q6U342LZ5KSXKZ3P2D5T2XLK6X8DAPK5GZMMNU2ELVPM45U4QDRM8E3CL467VMVQCVD5ZVNQA5Q85LN6QBLW8GGL2ZHPDN2RN44UMM9VGQNNF7476E36CWDRXNMM7T56WMN4R37SGG9W3K42UPLLEXZ27BVE59R54RB8DGVXR83S7WQ88XKRUR

---

I would then share one each with people who know me and who I trust.

1. [@mix](@ye+QM09iPcDJD6YvQYjoQc7sLF/IFhmNbEqgdzQo3lQ=.ed25519)
2. [@Alanna](@6OxffMLNyxkboLjCqv29WnMPhH8O3qFrcXCR6KrKcPI=.ed25519)
3. [@Kieran](@MpDd66GPXgN1+eMNrZInHkWq1THMurWwLdMx8BZ1ncw=.ed25519)
4. [@mikey](@6ilZq3kN0F+dXFHAPjAwMm87JEb/VdB+LC9eIMW3sa0=.ed25519)
5. [@kate b](@LPPV2X+3A06pXkk5pn8XXfaJYMlDQiyLXlySaa9AdmQ=.ed25519) 

It would also be important that I think the community would also trust enough of these people...

---

Lets imagine that I get hit by a coconut whilst reading a book in Fiji (I grew up in rainy UK so never learnt that you never sit under a coconut tree with coconuts up there)

After some time I have been very quiet and a few people have noticed I am no longer putting up my cat pictures on the interwebz or on the buttz. [@mix](@ye+QM09iPcDJD6YvQYjoQc7sLF/IFhmNbEqgdzQo3lQ=.ed25519) sends me a signal message and keybase message, no game.   [@Kieran](@MpDd66GPXgN1+eMNrZInHkWq1THMurWwLdMx8BZ1ncw=.ed25519) knows my family who tell him that I have been hit by a coconut in the head and am in hospital and unconscious. Mix and Kieran are working on a project together & Mix has much mana within buttland so spreads the word that I have been coconutted. People organise to send a postcard and a care package (we can hope, right?!) and then Mikey, Alanna and Mix meet up physically to share the combine the secrets to recover the seed to the multisig wallet:

http://secrets.dyne.org/share

(Try it out! You can use any three of the above secrets to recover the intial data)

---

The process for setting up a new multisig wallet could start and the funds from the old wallet could be moved to the new wallet.

There are some rough edges to be polished on the process - but I hope you can see where I am coming from.

e.g. it is likely best practice that the person sharing the secrets does not tell the participants who else is a secret holder. This allows plausible deniability for the $5 wrench problem. It would mean that once Mix found out from Kieran that I had been nutted, he would likely have broadcast that he was a secret holder and that other secret holders could contact him privately....

Voila
