# I will assist (50)
`File: dhcp.pcapng What IP address is requested by the client?`

Once opened in wireshark we can filter for DHCP protocol
a few of the the packets shown contain:
```
| No  | Source        | Destination     | Protocol | Info          |
|-----|---------------|-----------------|----------|---------------|
| 176 | 192.168.2.244 | 192.168.2.1     | DHCP     | DHCP Release  |
| 186 | 0.0.0.0       | 255.255.255.255 | DHCP     | DHCP Discover |
| 188 | 192.168.2.1   | 192.168.2.244   | DHCP     | DHCP Offer    |
| 189 | 0.0.0.0       | 255.255.255.255 | DHCP     | DHCP Request  |
| 190 | 192.168.2.1   | 192.168.2.244   | DHCP     | DHCP ACK      |
```
We are seeing a source asking for an IP and the source address is 192.168.2.244 so this is the flag