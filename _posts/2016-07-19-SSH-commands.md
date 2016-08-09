---
layout: post
title: SSH - commands
---

I use a headless Raspberry Pi as a central location from which I connect to other remote servers. By doing this, I can keep a single screen / tumx session open 24/7 and attach to / detach from it from various different locations (work, home or phone). I also open SSH port tunnels to this Raspberry Pi, and from there open further SSH port tunnels (using the below commands) to other remote servers allowing me to jump between different networks very quickly.

Simple SSH connection

    ssh <user>@<host>


Use a specific remote port (-p)

    ssh -p <remote-port>  <user>@<remote-host>


Using a private key (-i)

    ssh -i /path/to/private-key.pem  <user>@<remote-host> 


Open an SSH port tunnel that is available on the localhost (-L)

    ssh -L <local-port>:<tunnel-to-host>:<tunnel-to-port>  <user>@<remote-host>


Open an SSH port tunnel that is available on the local network (-g)

    ssh -g -L <local-port>:<tunnel-to-host>:<tunnel-to-port>  <user>@<remote-host>


Open an SSH port tunnel without a shell (-N)

    ssh -N -L <local-port>:<tunnel-to-host>:<tunnel-to-port>  <user>@<remote-host>


Execute a command (on the remote host) once an SSH connection is successful

    ssh <user>@<remote-host> 'ls -l'


Execute a command (on the remote host), that you will interact with, once an SSH connection is successful (-t)

    ssh -t <user>@<remote-host> 'screen -xR'


Finally, an example of what I use

    ssh -t -g -L 8080:192.168.1.1:80 -p 9980 dmulligan@myserver.com 'screen -xR'


Which I have setup as an alias

    alias pi="ssh -t -g -L 8080:192.168.1.1:80 -p 9980 dmulligan@myserver.com 'screen -xR'"


