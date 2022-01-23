# A very secure authentication method (100)
`File shell.pcapng What password is used to elevate the shell?`

When we look at the shell again, port 4444, we can see every time a sudo command is run just before we see:
```
jtomato@ns01:~$ echo "*umR@Q%4V&RC" | sudo -S apt update
echo "*umR@Q%4V&RC" | sudo -S apt update
```
So this is most likely the password.