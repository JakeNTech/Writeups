# Tick tock (50)
`File network.pcapgng What is the NTP server IPv6 address?`

Doing a bit of reaserch suggests that NTP is a protocol related to time; I knew that time servers are a thing, but didn't realise that they had their own protocol before, (I bet I can amaze you with the stuff that I don't know!), we can filter for this in Wireshark.

Now we can see 10 packets, but we are after an IPv6 address, and their are two packets that show IPv6 Addresses in the source and destination columns, although its more than proberbal that this is a red herring; however:
```
| No.  | Source                     | Destination                | Info                  |
|------|----------------------------|----------------------------|-----------------------|
| 2918 | 2003:51:6012:121::10       | 2003:51:6012:110::dcf7:123 | NTP Version 4, Client |
| 2919 | 2003:51:6012:110::dcf7:123 | 2003:51:6012:121::10       | NTP Version 4, Server |
```
The source of the packet with the info `NTP Version 4, Server` is presumable the NTP server's address. 