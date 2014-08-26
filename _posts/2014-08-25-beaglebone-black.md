---
layout: post
title: "BeagleBone Black"
date: 2014-08-25 21:08
comments: false
categories:
published: true

---
When I originally got the idea of starting this blog, I didn't want to have to spend lots of money on it (i.e. monthly billing for cloud hosting) as it would only be for hobby purposes and I never expect to drive much traffic.  For reasons detailed in the previous post, it was a hard thing to come by and self-hosting seemed to be the better route.  Some people host directly on their computers but I mainly work off a laptop, making the projected up-time laughable.  There's also an old Pentium 4 desktop laying around but I didn't want to suffer through the winding fan noise and hike of electric bill for what I was going to do with it.

A few years ago [single-board computers](http://en.wikipedia.org/wiki/Single-board_computer) gained mass popularity in the DIY community with the release of the [Raspberry Pi](http://www.raspberrypi.org), featuring an ARM based SoC for the low price of $35.  The I/O ports featured would cover the minimum needed for the job.  A year later (and only a few months before I started looking into this), Texas Instruments released the [BeagleBone Black](http://beagleboard.org/black), the least expensive version of their BeagleBoard line.  It was featured at $10 more than the Pi, but offered a 1GHz CPU vs the 700MHz on the Raspberry Pi and faster RAM.  The GPIO ports that these boards offer didn't interest me and although the Raspberry Pi had better graphics capabilities, I decided it wasn't important for what I wanted to do (a decision a would later regret while looking into fitting it as an HTPC).

What set these boards apart from alternatives such as the popular Arduino line of products, is the possibility to run Linux on them.  One of my priorities while looking for server capable hardware.

I currently use it as a NAS, a web server for Static Brace as well as a DLNA media server for streaming to the TV via the PS3.  I'll detail how I got these setup in an up-coming post but for the time being, I'll simply point out that it fills these needs like a champ.  While idle, the CPU averages 3% usage as well as 180MB/495MB of RAM.  While streaming, the CPU averages ~10% usage and RAM is barely affected, leaving plenty of overhead<sup>1</sup> for other tasks.  

For anyone else looking for a simple and cheap setup for hobby projects and require some sort of system to serve as a light server, I would definitely recommend the BeagleBone Black.  There are drawbacks which required workarounds however, but it will be detailed at a later time when I'll also explain the choice of software I have running on the server.

<!---
//Use for next post

After setting on the BeagleBlack, I needed an operating system.  The board comes pre-loaded with the Ångström Linux distribution but I had already decided that I would replace it with Debian because of my familiarity with it, its legendary stability and exhaustive software repository.

The hardest part of the initial setup was getting the Debian running on an ARM based system.  Thankfully, the elinux wiki had [well detailed instructions](http://elinux.org/BeagleBoardDebian).
-->

- - -
<sup>1</sup> It remains obvious that this small budget-focused server can't compete with real server grade hardware.

