# Please give (50)
`File network.pcapgng What is the IP address that is requested by the DHCP client?`


After loading the file we can filter for the DHCP protocol, and there is the request/offers:
```
| No   | Source  | Destination     | Protocol | Info         |
|------|---------|-----------------|----------|--------------|
| 1254 | 0.0.0.0 | 255.255.255.255 | DHCP     | DHCP Request |
```
When we examin this packet:
```
Option: (50) Reqested IP Address (192.168.20.11)
	Lenght: 4
	Requested IP Address: 192.168.20.11
```
and so we have the answer!