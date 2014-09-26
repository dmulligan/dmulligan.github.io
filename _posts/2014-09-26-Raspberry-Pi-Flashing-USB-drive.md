---
layout: post
title: Raspberry Pi - Flashing USB drive
---

I recently sold my MacBook Air and shortly afterward the USB flash drive that I use to boot my FreeNAS server got corrupted leaving me in an awkward position of not having any easy way of recreating a new USB flash drive. I still, however, had my Raspberry Pi server which should have no problem writing a FreeNAS image to a USB flash drive. Here were the steps I used to get the job done.

1. Download the FreeNAS USB image

		wget http://download.freenas.org/9.2.1.7/RELEASE/x64/FreeNAS-9.2.1.7-RELEASE-x64.img.xz
  
2. Identify the correct /dev path to your attached USB flash drive. There are a few different ways to do this

		mount, lsusb, fdisk, dmesg, /var/messages or /dev/disk/by-id/usb-*

3. Update the /dev path to the USB flash drive in the following command and execute it (My USB flash drive is /dev/sdb)

		sudo sh -c 'xzcat FreeNAS-9.2.1.7-RELEASE-x64.img.xz | dd of=/dev/sdb bs=64k'
