# What version pt. 2 (100) - UNSLOVED
`File shell.pcapgng What is the OS version name of the target system?`

From looking at the shell on port `4444` the user installs netcat:
```
jtomato@ns01:~$ echo "*umR@Q%4V&RC" | sudo -S apt update
echo "*umR@Q%4V&RC" | sudo -S apt update

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease
Hit:4 http://us.archive.ubuntu.com/ubuntu bionic-security InRelease
```
From this we can see that it's most likely a debian/ubuntu system and from a quick google search it would appear to be `Ubuntu 18.04.4 LTS (Bionic Beaver)` https://releases.ubuntu.com/18.04/  However I am not all to confident that this is the actual answer