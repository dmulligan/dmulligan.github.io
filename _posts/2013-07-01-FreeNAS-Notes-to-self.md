---
layout: post
title: FreeNAS - Notes to self
---

Here are some notes about doing simple stuff via SSH in FreeNAS, my memory isn't quite what it used to be.


Mounting FAT USB drive
----------------------

First, find out the path to your USB drive by executing dmesg and reivewing the output.

		$ dmesg

		ugen1.2: <Seagate> at usbus1
		umass1: <Seagate GoFlex Desk, class 0/0, rev 2.10/1.00, addr 2> on usbus1
		da1 at umass-sim1 bus 1 scbus7 target 0 lun 0
		da1: <Seagate GoFlex Desk 0D18> Fixed Direct Access SCSI-5 device
		da1: 40.000MB/s transfers
		da1: 1907729MB (3907029167 512 byte sectors: 255H 63S/T 243201C)

From the above, you can see that the USB drive is located at /dev/da1, now look for the paritions on that drive using:

		$ ls -l /dev/da1*
		crw-r-----  1 root  operator    0, 143 Jun 30 05:01 /dev/da1
		crw-r-----  1 root  operator    0, 144 Jun 30 05:01 /dev/da1s1

We know know that the first partition is located at /dev/da1s1, next we can try to mount that drive

		$ mkdir usb-drive
		$ sudo su
		$ mount_msdosfs /dev/da1s1 usb-drive

If you have a USB drive is a large FAT partition, you will need to add the '-o large option' to the command.

		$ mount_msdosfs -o large /dev/da1s1 usb-drive

