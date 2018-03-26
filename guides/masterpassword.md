# Master Password Setup and Recovery Guide

This guide is an opinionated guide to getting started with a password manager. We've chosen MasterPassword.

### Why MasterPassword?

Other password managers like KeePassX or 1Pass require you to store a password database. Unlike these, MasterPassword uses cryptography to magically recover your unique passwords based on 3 main conditions.

Your name -- e.g. _Rumplestiltskin_ :imp:

Your master passphrase -- e.g. `mysupersecretmasterpassphrase`

The sitename -- e.g. `github.com`

This means that you will have to remember your name, your master password, and the formatting for your the way in which you enter the sitename.

**What you will need:**

- Your own computer :computer: or smart phone (Android/iPad)

## Overview
1. [Installation](#1-installation)
1. [Store a password](#2-store-a-password)
2. [Recover your password](#3-recover-your-password)

## 1. Installation

Android | iPhone / iPad | Windows / Linux | Mac | Any
:-------|:--------------|:----------------|:----|:----
Google Play Store | iStore | [Java .jar installer](https://ssl.masterpasswordapp.com/masterpassword-gui.jar) | [zip installer](https://ssl.masterpasswordapp.com/masterpassword-mac.zip) | [web app](https://js.masterpasswordapp.com/)

Select the relevant installer.

**Windows**
* Open nodepad
* Copy the code from the `.jar` file into your nodepad file
* Save the file with extension `.bat`
* Double-click on the `.bat` executable

**Linux**
* Run the `.jar` file with `java -jar /path/to/file.jar`

**WebApp**
* Right click and save the HTML page locally
* Disconnect from the internet
* Open the `index.html` file

_TODO:_ MacOS

## 2. Store a password

* Enter name and master (memorizable) passphrase
* Create new entry with sitename `mmt_bitcoin_multisig`
* Ensure you choose the same algorithm type across platforms. The default option is V3 (at time of writing is the most recent). 
* Ensure you choose `Maximum Security` or `GeneratedMaximum`. The name of this may vary across the platform you've installed MasterPassword on. Choose the one that produces the longest password.
* It should auto generate your password as you type. When you've done the above steps, your password is complete.

Depending on the platform you've installed MasterPassword on, you may have to recover your passphrase each time. On the Android App, it will save and when you 'log back in', the stored sites will be visible.

When using the `.jar` installer (which can be formatted as a Windows installer by copying the code into a `.bat` file and executing it), or the Web interface, you must re-enter these unique values each time, and it will generate your passphrase.

## 3. Recover your password
The magic of MasterPassword means that the method to [store a password](#1-store-a-password) are the same as the method to recover your password. If you've installed the android application, you simply re-enter your name and passphrase, your passwords will be visible in the dashboard.

* Enter your name and master passphrase
* Create a new entry with the sitename your remember, for example `github.com`
* Select V3 algorithm type.
* Select `Maximum Security` or `GeneratedMaximum`.
* Copy the password

---

Congratulations, you're now using a password manager! :sparkles: :space_invader:
