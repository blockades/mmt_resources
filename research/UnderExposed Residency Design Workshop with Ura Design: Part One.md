# UnderExposed Residency Design Workshop with Ura Design: Part One

tags: #peer-research #darkcrystal #dark-crystal-research #dark-crystal-feedback #underexposed #simplysecure #ura-design

ssb cypherlink: %QqKBQTL0hoslzjFMWwBInwO660RFvb41PKI/taqa22E=.sha256

![](https://i.imgur.com/6hd0m8k.png)

[Sierra Magazine "The Quran in My Backpack"](https://www.sara-alfa.com)

_image caption: a richly colorful picture from the perspective of a person of color holding a book on their knees. They are wearing skinny fit grey trousers and white pointed fancy shoes. They are wearing a mustard colored shirt or jacket of which you can only see the cuffs with a light blue coloured patterned shirt popping underneath. They have some red beads around their left hand wrapped around their index finger (perhaps they are Tasbih (prayer beads)). There is a tiny world scene literally popping out of the book, like the book holds a world. There are red mountains at the top right surrounded at the base by a jungle of green trees. There is also a lake which is blue. There are clouds at the top of the mountain (well above the book). This mountains, forrest, cloudy landscape unfolds through the left side of the book also. Lastly the fabric red bookmark is flapping as if from wind emerging from the scene in the book. It's magical._

## Preamble

This is the second in a series of reflections about Simply Secure's [UnderExposed 2019 Residency](https://simplysecure.org/underexposed/).

For this user testing we just used Dan Hassan's computer and dove right in so that we could look at the actual design rather than the user experience of onboarding. This piece as a companion plant for Kieran's [Peer Research document](https://github.com/blockades/mmt_resources/blob/master/research/dark_crystal-report_peer_testing_and_usability_assessment.md) ([cypherlink](%Rbg6Gr19sYSXgxYf8CxqGTSe5oelR0M0HwAxh62Q1eo=.sha256)). We think of the other humans involved as Peers rather than Users.

## What is Dark Crystal 

[Dark Crystal](https://darkcrystal.pw) is a social secret backup application, built on the peer-to-peer protocol Secure-scuttlebutt and also using Shamir's secret sharing algorithm. It is similar to [dyne](https://dyne.org)'s [Secrets](https://github.com/dyne/FXC) and [Freedom of the Press Foundation](https://freedom.press)'s [Sunder](https://github.com/freedomofpress/sunder) 

In the release post for Sunder https://freedom.press/news/meet-sunder-new-way-share-secrets/ they state:

> Furthermore, any secret sharing implementation is only as robust as the operational security around it. If you distribute or store shares in a manner that can be monitored by an adversary (e.g., online without the use of end-to-end encryption) this could compromise your security.

It's this surrounding operational security which we have been researching by developing on top of scuttlebutt, which is offline first and P2P. We are researching existing techniques and strategies used by software tools for documenting human rights abuses and whistle blowing, in particular the following areas:

- Management of data and encryption keys after loss of theft of device(s).
- Resilience to poor or absent internet connection.
- Mechanisms for remote share revocation.
- Systems tolerant to error of data storage.

## Purpose of this Post 

In this Post I am specifically focusing on feedback relating to the creation of a new dark crystal. 

## Ura Design peer testing and design session

![](https://i.imgur.com/PJMWJ3n.png)


_image caption: a screenshot of the Ura Design website. There are two panels laid horizontally side by side. The left pane is blue (a rich blue, not sky blue, maybe it's called royal blue?). Text in white on this left hand blue pane is "USABILITY AND OPEN SOURCE DESIGN: Ura supports Open Source and Free Software Projects with Usability, Visual Identity and User Experience Design, no matter if small grassroots or established enterprise." On the right pane is a picture of two males by a projector with three participants around a table - they look like they are in discussion._

We got to sit down with [Elio](https://twitter.com/elioqoshi) from [Ura Design](https://ura.design/). The first thing we did was to sit and run through how the current application works. We started with the Dark Crystal home page.

"Why isn't this called the home page?"

![](https://i.imgur.com/yI9WzzG.png)


_image caption: image of the /dark-crystal page in patchbay client for scuttlebutt. Center there is the header: DARK CRYSTAL with a small diamond logo. Underneath these as unclear tabs are "My Crystals, Others Shards and Others Crystals", "My Crystals" is underlined suggesting this is the view in focus (you can think of this as the Dark Crystal Home Page or Inbox). There is a 'NEW' button which is purple. There are long bright fluro pink thin rectangles as line items each with some text (in white) and on the left end of each rectangle is a date. One of the rectangles has the mouse hovering over it and it has changed to dark purple._ 

First question: "What are all these line items?"

The next question was: "What are My Crystals, Others Shards and Others Crystals".

My first attempted explanation was: "You want to keep a secret safe and you want your friend to help to keep the secret safe in case you lose your computer. This tool allows you to transform your secret into shards (pieces). Each shard is useless by itself so each person holding a shard knows nothing about the nature of the original secret. To recover the original secret a minimum number (threshold) of these shards will need to be recombined to recover the original secret. If you're into Harry Potter - think Horcrux."

Ok... in principle. Easier to show what I am talking about. We'll get back to "My Crystals, Others Shards and Others Crystals" in part two.

![](https://i.imgur.com/ixzc0fl.png)

_image caption: a new window overlays the previously described inbox/home page view (which has changed to a light purple hue). The new window is a black box taking up the center of the page which says "New Dark Crystal". There are 5 input boxes (with purple background). The first box has "Name" as a label on the left and there is some helper text in the input box which says "a short name for this crystal". Next "Label" with helper text "a more detailed description for furture you/family who might recover this". Next "Secret" with helper text "your secret". Next "Custodians" with helper text "those you trust to guard your secret". Lastly "Quorum" with helper text "number of shards recover". At the bottom of this New Dark Crystal window is a "Cancel" button and a "Perform Ritual" button._

After filling in...

![](https://i.imgur.com/0Fvt0av.png)


_image caption: this is the same view as the previously described image but with boxes filled as so: "Name: this is a demo for the blog piece", "Label: this is a label which will be seen by the custodians", "Secret: this is super top secret don't tell anyone. i prefer vegemite.", Custodians: Peg (a mouse avatar), Alanna (Alanna in a zebra outfit taking a selfie in the mirror avatar), mu (a blank turquoise square avatar), mix (mix standing on a rock with a blue sky behind him avatar), kieran (kieran silhouette standing on a rock at night with an amazing star scape in the background avatar)", "Quorum: 3". Having filled all this in the "Perform Ritual" button is now purple (for happy, click me!)_

After running through the interface and going through each box. Elio pointed out that there is a conceptual weakness in the Information Hierarchy of our current design. All the input boxes are the same background colour and the same size. This is confusing and doesn't highlight the following functions**

- [1] data which will stay local and never leave your computer (NAME)
- [2] data which will be transmitted but will not be encrypted (LABEL)
- [3] data which will be transmitted _and_ encrypted (SECRET)
- [4] information about who knows about who (CUSTODIANS)
- [5] information about the implications of different thresholds (QUORUM)
- [6] information about the network and gossip replication is absent 

The point being that there should be a clear difference between data which is staying local (thus only available to the owner) and information which is being sent across the network. That information which is going across the network it should be clear about what is encrypted and what is unencrypted.

All this is a long way to confirming the tool is not yet intuitive. But we all know that already :)

Additionally it's not clear how many steps there would be in this process, how far through are we, what happens when you click 'Perform Ritual', is it possible to go back if you change your mind about something. In the wider P2P realms this forecasting and orientation is all the more important given the gravity of immutability. This is an emergent accessibility issue in blockchain and beyond where we are requiring that peers understand that some actions are truly irreversible. With this in mind then Elio suggested adding a subsequent step which shows all the options which have been selected and perhaps has an written description of what this means. Perhaps also an chance for a visual diagram. That paragraph would go something like:

> "Your local name for this crystal is XYZ - this will show up in your home page, its local data for you to remember this crystal (but remember if you lose your computer it won't be part of what your friends can give back to you).

> The label which is being passed unencrypted to your friends is ABC. They'll be able to read that and this will also be passed to you when you request your shard back. 

> You're about to encrypt this SECRET. When you confirm this dialogue it won't live in this software any more - it will just live on your friends computers in this software in shard form.

> You're quorum (the number of people who will have to return their shard for you to recover the whole) is 2. You must trust this group ALOT! That means any two of them could recover the whole. The Custodians don't know who eachother are though, but it can be assumed the other Custodians will assume it will be one of your scuttlebutt friends. They also don't know how many shards are needed to recover the whole and they don't easily know how many other people are custodians within this crystal (this could however non-trivially be determined using simple metadata analysis if you know the timestamp of one of the shards.)"

I know this is alot of info - but you get the drift. It's a moment where people can think about their options and tweak if needed.


Importantly it was not clear within the interface that the SECRET would not be stored within Dark Crystal locally on the peers machine, that it would only exist in sharded form on our Custodians computers.

![](https://i.imgur.com/BagMEso.png)


_image caption: this is the dark crystal home view again but this time with a new line item for the crystal that was just created_

Lastly Elio reminded me that it's important to be kind to peers and to understand that using new tools is daunting. The domain of Dark Crystal is that of important and precious information with gravity to the consequences. Upon completion of the formation of the Crystal we are returned to the Dark Crystal home view. Elio suggested that we make it really clear that the process has worked. One simple way to do this might be to take the peer straight into the Crystal view for the created crystal with a nice notification congratulating the peer for successfully sharing their secret.

![](https://i.imgur.com/H0wpe7E.png)

_image caption: this is a new view. a new tab has opened in the software. Title is Dark Crystal with the logo. Under this is a black box with all the avatars of of the people involved in the locally named "this is a demo for the blog piece" crystal. To the right of the custodians avatars is the quorum which is 3. Under this box is a History label and each of the custodians is a line item underneath with their own rectangle box. On the left is the custodians avatar, in the middle is a small right pointing arrow with a crystal icon (the same as used for the main Dark Crystal logo) with "Shard sent". On the left there is a purple "Request" button_

Elio was slightly confused why we have hover actions rather than just having the dates of shards sent and shards requested visble without hovering. 