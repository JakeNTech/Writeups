# Uh uh uh (75)
`File smb.pcapng What is the hex status code when the user SAMBA\jtomato logs in?`

Filtering for `SMB2` again we can see that there are two sets of `Session setup`s  one of the sets fails and the other goes through, the first (that failes) is for user `SAMBA\jtomato` and the second, says, if for `\` but the hex status code (The one that is in the return packet from the first request):
```
NT Status: STATUS_LOGON_FAILURE (0xc000006d)
```
So we have the code