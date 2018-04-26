# Withdrawl of BTC funds using Kraken and Revolut

This guide is an opinionated guide on how to smoothly transition your Bitcoin (or other crypto-currencies) into GBP or another fiat currency (see table below for a list of currencies Revolut will change into). **No conventional bank accounts required**.

**What you will need:**
* a computer :computer:
* a smart phone :phone:
* a delivery address :house:
* a bitcoin wallet :purse:
* some bitcoin :moneybag:
* some waiting time (a few days) :clock1:

:bulb: If you have not yet got a Bitcoin wallet, refer to [Bitcoin Beginner](./bitcoin-beginner.md) to learn how to setup an Electrum wallet, or if you're a group wanting to setup a collective wallet and use your bitcoin to pay for collaborative projects (which is totally rad!), refer to our [Bitcoin Electrum Multisig](./bitcoin-electrum-multisig.md).

**What we recommend:**
* a password manager :key:

:bulb: Please refer to [Bitcoin Beginner](./bitcoin-beginner.md) for a quick guide on how to setup KeePassXC or to [Master Password](./masterpassword.md) for a guide on how to use a more complex password manager.

**Additional extras:**
* a bank account

| Currencies Supported by Revolut | ed. 27/04/2018 |
|----------------------------------:|--------------------------------------:|
| United Arab Emirates Dirham (AED) | Canadian Dollar (CAD) |
| Swiss Franc (CHF) | Czech Replublic Koruna (CZK) |
| Danish Krone (DKK) | Euro (EUR) |
| Great British Pound (GBP) | Honk Kong Dollar (HKD) |
| Hungarian Forint (HUF) | Israeli New Shekel (ILS) |
| Indian Rupee (INR) | Japanese Yen (JPY) |
| Moroccan Dirham (MAD) | Norwegian Krone (NOK) |
| New Zealand Dollar (NZD) | Polish Zloty (PLN) |
| Qatari Rial (QAR) | Romanian Leu (RON) |
| Swedish Krona (SEK) | Singapore Dollar (SGD) |
| Thai Baht (THB) | Turkish Lira (TRY) |
| United States Dollar (USD) | South African Rand (ZAR) |

## Overview of Steps

1. [Setup a Kraken account](#1-setup-a-kraken-account)
2. [Install Revolut](#2-install-revolut)
3. [Send Bitcoin to Kraken](#3-send-bitcoin-to-kraken)
4. [Exchange Bitcoin to Euros](#4-exchange-bitcoin-to-euros)
5. [Send Euros to Revolut](#5-send-euros-to-revolut)
6. [Exchange Euros to another currency](#6-exchange-euros-to-currency)
7. [OPTIONAL: Send currency to a bank account](#7-send-currency-to-a-bank-account)

:bulb:
  - if you're unclear on anything, please ask.
  - :warning: = `this is a dangerous step, follow it exactly`
  - if the images are too small, make the text on your browser bigger
    - e.g. `ctrl + "+"` or `cmd + "+"`

---

## 1. Setup a Kraken Account

We recommend you setup using KeePassXC or another password manager [(as mentioned above)](#L25).

* Navigate to [https://www.kraken.com](https://www.kraken.com)
* Create an account, setup two factor authentication (either using SMS or we recommend [Authy](https://authy.com/).

We'll need to get you verified up to Tier 2 in order to withdraw fiat currency. Kraken will verify the identity of the user by cross referencing a name with an address.

The required details for Tier 1 & 2 are:
* Full Name
* Date of Birth
* Country of Residence
* Phone Number
* Address

This will enable you to withdraw up to $2000.00 a day, with a monthly withdrawl limit of $20,000.00.

If you need to withdraw more quickly, you'll have to complete the latter stages of verification which will require proof of identity. **This is not necessary for this guide**.

:warning: Do **not** do this through an anonymising proxy service such as Tor. Kraken will detect this and you will never pass the second stage of verification, meaning you have to recreate a new account. I have not tried using a VPN service such as OpenVPN or ProtonVPN. It may be that these work if you want to add a layer of security.

---

## 2. Install Revolut

In this section we'll simply follow the Revolut install/sign-up steps.

* Navigate to [https://www.revolut.com](https://www.revolut.com) on your smart phone.
* Hit 'Get the App', enter your phone number and you will receive a download link to install the Revolut App.
* Follow the steps to setup your Revolut account.

---

## 3. Send Bitcoin to Kraken

In this section you will need:
* Your Bitcoin Wallet with some Bitcoin
* To be signed in to Kraken

* On Kraken, navigate to the 'Funding' section, select 'Deposit', then Bitcoin (XBT) (or your relevant currency), and generate a new address.

![]('./assets/kraken-generate-bitcoin-address.png')

* Navigate to your Bitcoin wallet (Electrum, Samourai, Copay), and send the amount you want to transform into EUR to the address Kraken gave you.

:warning: Pay close attention, double check you've copied the address properly. Being sloppy here will lose your money

* Bitcoin transactions can take up to an hour or two to clear, so be patient.
* It will require a few confirmations before Kraken will release the funds to you in their system.
* You can double-check your transaction by visitng a blockchain explorer such as [OXT.me](https://oxt.me) or [blockchain.info](https://blockchain.info). Simply input the address to see the status of the transactions.

---

## 4. Exchange Bitcoin to Euros

In this section we will create a sell order in Kraken to exchange your Bitcoin (XBT/BTC) for EUR.

* Once you have received the funds in Kraken, navigate to 'Trade', select 'New Order', and input the amount of Bitcoin (XBT/BTC) you want to sell for EUR and create a sell order.
* Wait for the transaction to clear. This shouldn't take longer than an hour. If the order fails you may have to cancel and try again.

---

## 5. Send Euros to Revolut

In this section we'll need to create a destination withdrawl account in Kraken, so we'll need the account details from Revolut. These can be found by clicking the abacus icon in the _top-left_ corner of the Revolut App, selecting EUR and using the 'Local' details. You'll also need to find the office location for Revolut.

```
Revolut Limited
Level 39, One Canada Square
E14 5AB London, United Kingdom
```

:bulb: Above address at time of writing 27/04/2018. Check with [Revolut](https://www.revolut.com) see if this has changed.

* In Kraken 'Funding', select 'Withdraw', select 'EUR' and 'Add Account'.
* Set description as 'Revolut'
* Enter the relevant account details Revolut gave to you.
* Once saved, select Revolut in the dropdown on [the EUR withdrawl page](https://www.kraken.com/u/funding/withdraw?asset=ZEUR). Enter the amount of currency you want to send and hit 'Send'!

![]('./assets/kraken-sepa-withdrawl.png')

:bulb: Kraken will send you a confirmation email within an hour or two. You will need to click the link to confirm the withdrawl.

Your money should arrive in Revolut within a day.

:fireworks: If you just wanted EURO's, you've finished the guide. Unless you want to send to your bank account, in which case, skip to [Send currency to a bank account](#7-send-currency-to-a-bank-account). :fireworks:

---

## 6. Exchange Euros to another currency

In this section we will exchange the EUR we have sent to Revolut to GBP (or the currency of your choice). This is a simple process which Revolut was designed for.

* First you will have to add your destination currency in Revolut, in the _top-left_ corner select the abacus icon, add an account and select GBP.
* On the home screen, select the EUR account in the top navigation tab, and hit the exchange spinner icon in the middle.
* Select the amount you wish to exchange and the destination currency GBP.
* Hit exchange!

:fireworks: Tada! You have exchanged from Bitcoin to the currency of your choice with low transaction fees, avoided the Coinbase beast, and without a bank account! If you already have the Revolut card, you can now spend this over the counter. To send to your personal or a friends bank account, continue to the next step. :fireworks:

---

## 7. Send currency to a bank account

In this final section we'll send money from your Revolut account to a bank account of your choice. This again is a simple process and easy to repeat.

* Go to Revolut, hit the 'Payments' tab, and in the 'Out' submenu. Select 'To bank account'. This will take you to the 'Bank Transfer' page.
* Add a new beneficiary. Depending on the context, you will want to select 'Myself', 'Another Person' or 'a Business'.
* Complete the form with your account details.
* Return to the 'Bank Transfer' menu and select the beneficiary you just entered.
* Enter the amount and hit send.
* Enter your pincode.
* Input the two-factor confirmation code Revolut will send you by SMS.

:fireworks: Whoosh! You're done. Revolut will email / text you telling you how long it will take to arrive in your account. _It usually takes 4-5 days to process a payment_ :smiley: :fireworks:

---

# FAQ

**%%TODO%%**

**If you encounter any problems with the process, we'd love to hear about it! We hang out on [Scuttlebutt](https://www.scuttlebutt.nz/).**
