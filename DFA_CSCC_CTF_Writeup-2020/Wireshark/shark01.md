# shark01 (50)
`File: dhcp.pcapng What is the transaction ID for the DHCP release?` 

Opening the DCHP file we can filter for DHCP:
```
| No. | info          |
|-----|---------------|
| 176 | DHCP Release  |
| 186 | DHCP Discover |
| 188 | DHCP Offer    |
| 189 | DHCP Request  |
| 190 | DHCP ACK      |
```
As we need the transaction ID for the realse we need to look at that packet:
```
Dynamic Host Configuration Protocol (Release)
	Messsage Type: Boot Request (1)
	Hardware address length: 6
	Hops: 0
	Transaction ID: 0x9f8fa557
```