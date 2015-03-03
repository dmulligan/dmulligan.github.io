---
layout: post
title: Linux Satellite Receiver - Engima EPG issues
---

I setup my Linux satellite receiver (Vu+ Solo2) just over a year ago and it has functioned flawlessly since then, that is until this last week when I started having an issue with CrossEPG. My receiver is setup to automatically download 7 days worth of TV guide every night at 1 a.m. but no TV programs were displaying in the EPG guide! Downloading the EPG data manually appeared to complete successfully, but still no TV programs were displayed in the guide. 

A quick search around the Internet lead to the suggestion of deleting the EPG dat file from my HDD via SSH, but first stopping Enigma as the EPG data is also stored in memory, and would be rewrote to the HDD. Once the DAT file is deleted, restart Enigma and manually downloaded the EPG guide and all was good again. 

SSH to your Linux receiver and run the following commands:

		# Stop Enigma
		$ init 4

		# Delete the EPG DAT file (your path maybe different) 
		$ rm /mnt/hdd/crossepg/ext.epg.dat

		# Restart Enigma
		$ init 6

Went complete, you can download the EPG guide manually and all should be working agian.

Some other useful commands are that you can run via SSH are:

		# Update your install
		$ init 4 && opkg update && opkg upgrade && init 6

		# Take a screen grab of the current TV channel
		$ grab -o -p /path/to/screen-grab.png

