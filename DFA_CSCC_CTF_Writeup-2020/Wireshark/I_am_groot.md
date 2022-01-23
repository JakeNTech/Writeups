# I am groot (50)
`File smb.pcapng What is the tree that is being browsed?`

Looking arroundd the file we can see that both `SMB` and `SMB2` protocols are used; Filtering for them both shows that `SMB2`, looking at the packet info (summery) there are two that start:
```
Tree Connect Request Tree:
```
The first one that we see is:
```
| No. | info                                      |
|-----|-------------------------------------------|
| 124 | Tree Connect Request: \\192.168.2.10\IPC$ |
```
But the following packets suggest that either the connection wasn't successful or the user was denied seeing that tree. A few packets later show:
```
| No. | info                                             |
|-----|--------------------------------------------------|
| 133 | Tree Connect Request Tree: \\192.168.2.10\Public |
```
And the packets that follow would suggest that the connection was successful as there is a folder and file that is created here. So this is the tree being browsed.