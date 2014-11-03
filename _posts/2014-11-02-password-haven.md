---
layout: post
title: "Password Haven"
date: 2014-11-02 21:09
published: true
comments: false
categories: 
keywords: keepass, password, cloud
description: How to keep your passwords safe using a password manager

---

It's no secret that people don't like passwords.  They should be [long and complicated](https://www.xkcd.com/936/) to be worth anything and these days, we just have so many.  How should we manage them?  Some may find one good one that they like and use it everywhere (please don't do that).  The old-school user may have them all written down in a booklet kept in a physical safe.  Retrieving that booklet and transcribing each password by hand may quickly become tedious if you find yourself having to enter passwords multiple times a day.  What do you do if you are away with no access to said booklet but still need one of the passwords found inside?  

Password managers have become the [accepted](http://arstechnica.com/information-technology/2013/06/the-secret-to-online-safety-lies-random-characters-and-a-password-manager/1/) "[recommended approach](http://arstechnica.com/security/2013/07/how-elite-security-ninjas-choose-and-safeguard-their-passwords/)" to password management.  Not only can they keep them safe for you, but most password managers will generate random strings for you to use as passwords; saving you the trouble of having to come-up with a new one each time.  I myself have been using the open source [KeePass](https://en.wikipedia.org/wiki/KeePass) format for almost 2 years now, only recently figuring out the best way to go about it.

Before settling down, I gave some of the commercial offerings a try though.  More specifically, [Dashlane](https://www.dashlane.com) and [1Password](https://agilebits.com/onepassword).  Both of these services are well regarded and offer a relatively close feature parity once you've payed a recurring subscription or bought a license, respectively.  A bonus point to both of these is the new TouchID integration with iOS for quick and safe access to your passwords.  During the free trials however, I felt limited in the ways I could organize my passwords and the UI for both desktop and mobile interfaces let me down.  They did *look* good, but Dashlane especially was functionally unintuitive.  This led me to reconsider the big names and go back to my previous solution.

I had started using KeePass with [KeePassX](https://www.keepassx.org), a cross-platform port of the original [KeePass](http://keepass.info) written in [Qt](http://qt-project.org), while I was using Linux ([Fedora](http://fedoraproject.org), more specifically).  Later, on OS X, I discovered [MacPass](http://mstarke.github.io/MacPass/) and instantly fell in love with it because of its native look thanks to its use of the [Cocoa API](https://developer.apple.com/technologies/mac/cocoa.html).

The other step was getting my passwords onto the iPhone.  A simpler task if you use Android.

I was originally using BitTorrent Sync to get the keepass file to my phone and keep it in sync.  As my list of passwords grew larger I became weary of the fact that I didn't have a backup and that I had been keeping my \*.key file right alongside my \*.kdb file on the filesystem.  Sure, an added password kept the encrypted database somewhat safe.  But the aforementioned setup was bad practice and made me cringe.  I thought for a while for what should be the best solution and recently came-up with the following:

The *.kdb database is put in [Dropbox](https://www.dropbox.com).  Already encrypted using [AES-256](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard), I feel safe leaving it there with Dropbox's [2-factor authentication](https://en.wikipedia.org/wiki/Multi-factor_authentication) turned on (I recommend you do so for any service you use that supports it).  I originally wanted to keep using [Copy](https://www.copy.com) to sync the file, but they didn't offer 2-factor.  The key file itself is placed in a [SpiderOak](https://spideroak.com) shared folder.  The reasoning for this is two-fold:

1.	It doesn't keep all the eggs in the same basket.  
2.	It's a way to get a copy of the database and key file onto the phone all while keeping a third backup safe.

Lastly, once the rest is taken care of, [MiniKeePass](https://minikeepass.github.io) is used to view the database on the iPhone.  It's a little app that does the job.  Due to the iPhone's limitations, it becomes somewhat of a hassle if you want to edit the database on the phone and save the changes.  So I just use it as read-only.  Android users should have no problem using the database in read-write on their phones.

The solution is not perfect, requiring more work than other alternatives.  However, passwords have been giving me less of a headache ever since I've implemented this setup into my workflow and with my recent changes, have never felt safer. 