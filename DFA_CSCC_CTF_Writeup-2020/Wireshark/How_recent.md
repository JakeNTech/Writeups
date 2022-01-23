# How recent (75)
`File shell.pcapng What version of netcat is installed?`

Looking at the shell from the last challange:
```
jtomato@ns01:~$ echo "*umR@Q%4V&RC" | sudo -S apt install netcat
.
.
.
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 netcat all 1.10-41.1 [3,436 B]
.
.
.
Preparing to unpack .../netcat_1.10-41.1_all.deb ...
Unpacking netcat (1.10-41.1) ...
Setting up netcat (1.10-41.1) ...
```
so the answer is version 1.10-41.1