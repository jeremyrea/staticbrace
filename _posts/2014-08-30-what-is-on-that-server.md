---
layout: post
title: "What's on That Server?"
date: 2014-08-30 23:30
comments: false
categories: 

---
As I mentioned in my previous post, I'll detail here what software is used on the BeagleBone Black to fill-in specific needs and why I chose them.  Some appear obvious while others are the fruit of trial & error and research.  

##OS
After setting on the BeagleBlack as the server, I needed an operating system.  The board comes pre-loaded with the Ångström Linux distribution but I had already decided that I would replace it with [Debian](https://www.debian.org) because of my familiarity with it from previous desktop usage, its legendary stability and exhaustive software repository.

The hardest part of the initial setup was getting Debian running on an ARM based system.  Thankfully, the elinux wiki had [well detailed instructions](http://elinux.org/BeagleBoardDebian).  You'll have the choice to run off of the microSD card, or to flash the onboard eMMC memory (limited to 2 GB).  I chose to flash the eMMC.

**NOTE:** Take note that if you run off of the microSD card, you'll have to hold-down the USER/BOOT button every time the system boots to tell it to boot off of the external card or else it won't boot.  Not a practical limitation to have if the server reboots from a power outage and you're not there.

The downside to flashing the eMMC is that you are limited in space.  I am still figuring out a way to expand the available storage onto the microSD card.  I'm currently at 400MB of free space, only after having reached 100% capacity a few weeks ago and learning the hard way to never let that happen again.  

I'll update this post in the future if ever I successfully expand my available storage.

##Web server
In the instance you've already landed on a 404 page of this site, you'll have surely already noticed that Static Brace is powered by Nginx.

I had heard of Apache in the past and was aware that it was a battle tested HTTP server, dating back to 1995.  I however did some research before setting things up to make sure it was the right choice.  I eventually landed on Nginx, a newer piece of software released in 2002, which has received much praise.  Multiple accounts state that it is faster at serving static files, making my decision clear.

If setting-up your own website is something you'd like to do, I have to strongly recommend the [Web Served](http://arstechnica.com/series/web-served/) article series on Ars Technica.  It is incredibly detailed and will walk you through the various steps of installing and configuring the different building blocks of a web server.

##Home Media Server
The BeagleBone needed to be able to serve media to the PS3 to have it viewable on the TV.  I had used [PS3 Media Server](http://www.ps3mediaserver.org) in the past on a desktop to view one-off files and it worked quite well.  It did work on the BeagleBone as well, although not so much for HD content.  See, PMS transcodes the video files before pushing them to the client (PS3).  In the case of HD content, the server couldn't keep up and it'd just be a stuttering mess.

I obviously needed something else if I wanted to view these 1080p files with the PS3.  [miniDLNA](http://sourceforge.net/projects/minidlna/), available in the Debian repo's, is a "lightweight DLNA/UPnP-AV server targeted at embedded systems".  The lightweight aspect was very much important while comparing it to the popular [MediaTomb](http://mediatomb.cc).  miniDLNA fit the bill to serve-up HD videos to the PS3.  But here's the catch: it won't be able to play the large selection of video formats like PMS does because it doesn't take care of encoding, so you're left to comply with [file formats compatible with the PS3](http://manuals.playstation.net/document/en/ps3/current/video/filetypes.html).  Leaving-out the all-too-popular MKV's.  That being said, if the file format is compatible, the PS3 will play your 1080p videos without a hitch.

So to make my library playable, I've had to go in and re-encode the incompatible ones using [ffmpeg](https://www.ffmpeg.org) (not available in the latest Debian repo's).  There is abundant documentation and QA's that will help you find the flags that you'll need to set.  If you'd like to do a batch conversion, you can run a loop in the command line, here's an example:

	for file in *.avi; do ffmpeg -i "$file" -OPTIONS "${file%.avi}.mp4"; done
	
Where "file" is the variable name, and * acting as a wildcard.

##iTunes server
I most often listen to my music while at the computer with headphones on.  While I enjoy watching movies on the couch in front of a big screen, my music is best served at my desk.  As much as it pains me, iTunes must be the client.  Getting any outside piece of software to work with iTunes is no easy task.  I had initially given forked-daapd (a fork of mt-daapd) a shot, unfortunately it would stop working whenever I'd put the music on pause for more than a few seconds and I'd have to go restart the service manually causing a whole rescan of the library (which takes hours due to its size).  This became tiresome and impractical after a few months so I instead simply pointed the iTunes Library directly to my music collection on the network drive.  

It seems to be doing the job for the time being.

##Print server
This is incredibly useful if you have multiple computers to connect to a single printer for example.  Luckily, Debian's [System Printing](https://wiki.debian.org/SystemPrinting) part of the wiki has all you need to get things running and it is really easy.  Your mileage might vary however depending on your printer model and available drivers.

##Closing comments
This may all seems like a lot for the little single-board computer, but so far the BeagleBone Black has hung in there.  It's still good to note that printing does not require much resources.  It's also rare that I listen to my music while simultaneously streaming a movie.  The bottleneck in this case would be the HDD, with the disk head having to continuously switch between 2 files.  Finally the website isn't driving significant amounts of traffic at the moment and so hasn't been pushed to its limits yet.

As I've mentioned in the previous post, this setup fulfils it's needs nicely; offering convenience at a minimal cost.  At the same time, it's been fun and a great learning experience (especially for the web server part) setting everything up.