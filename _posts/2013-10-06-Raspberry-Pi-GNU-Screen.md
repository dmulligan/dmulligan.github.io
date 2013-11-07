---
layout: post
title: Raspberry Pi - GNU Screen
---

I have a terrible short term memory and easily forget what I was doing just a few minutes, never mind hours ago. What's this post about again..... ah yes screen. I find this application incredibly useful for accessing persistence xterm sessions from different locations: home, work, my tablet / phone etc. It allows me to start long running processes, detach and the process will continue running while I'm away. It's also useful in that it allows a number of terminals to open using the one SSH connection. I normally have a few terminals open at once across my Raspberry Pi, FreeNAS, CCTV camera etc.

I've tinkered with my ~/.screenrc file for a while now and am quite happy with it. It adds a persistence bar across the bottom of my terminal displaying some useful information including server name, open windows, and the current date and time. The time updates each minute, which in itself is useful as it stops idle connections from disconnecting.

The bar looks something like:

	19:55:08 rpicam:~$ 
		
		
		
	[rpi][      0$ bash  1-$ bash  2$ bash  (3*$bash)      ][06/11  7:56PM]


The contents of my ~/.screenrc file is:

	vbell off
	startup_message off
	hardstatus alwayslastline
	hardstatus string '%{= kg}[%H][%= %{= kw}%?%-Lw%?%{r}(%{W}%n*%f%t%?(%u)%?%{r})%{w}%?%+Lw%?%?%= %{g}][%{B}%d/%m %{g}%C%A]'

	termcapinfo xterm|xterms|xs|rxvt ti@:te@

	# Screen can persistently show window captions ("[Ctrl+A]: caption always").
	# [Ctrl+A]: caption always "%{= kB}%-Lw%{=s kB}%50>%n%f* %t %{-}%+Lw%<"


I have Putty setup to automatically connect to any existing screen session when a new SSH connection is opened. You can do this in Putty using the setting: Connection > SSH > Remote command: screen -xR

From then on, just remember to use 'Ctrl-a d' to detach from screen and exit Putty all at the same time.
