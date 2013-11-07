---
layout: post
title: Raspberry Pi - Samba
---

# Map Windows SMB share on Linux

First, ensure that the Samba client is installed on your Linux box.

	$ sudo apt-get install smbclient


Next, you need to create a local directory to use as a mount point and then mount the network shared directory to that location using a command similiar the following examples:

	$ sudo mkdir /mnt/nas-share/
	$ sudo mount -t cifs -o rw,file_mode=0777,dir_mode=0777 //nas/Share /mnt/nas-share/

	$ sudo mkdir /mnt/nas-protected-share/
	$ sudo mount -t cifs -o user=USERNAME,password=PASSWORD,rw,file_mode=0777,dir_mode=0777 //nas/ProtectedShare /mnt/nas-protected-share/


The command arguments used:
- -t cifs - use the CIFS mount file type
- -o
	- rw - mount as read-write
	- file_mode - If the server does not support the CIFS Unix extensions this overrides the default file mode
	- dir_mode - If the server does not support the CIFS Unix extensions this overrides the default file mode
	- user - specifies the CIFS username to connect as.
	- password - specifies the CIFS password. If not specified, you will be prompted for it.
