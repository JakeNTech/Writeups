# Who speaks (50)
`File: dhcp.pcapng What is the MAC address of the client?`

Once again applying the DHCP filter and we need to look at the packets with the source from the machine not the server, once we have chosen one, you have a choice of three, we can examin it:
```
Dynamic Host Configuration Protocol (Offer)
    Message type: Boot Reply (2)
    Hardware type: Ethernet (0x01)
    Hardware address length: 6
    Hops: 0
    Transaction ID: 0x2a7d544b
    Seconds elapsed: 0
    Bootp flags: 0x0000 (Unicast)
    Client IP address: 0.0.0.0
    Your (client) IP address: 192.168.2.244
    Next server IP address: 0.0.0.0
    Relay agent IP address: 0.0.0.0
    Client MAC address: VMware_82:f5:94 (00:0c:29:82:f5:94)
    Client hardware address padding: 00000000000000000000
    Server host name not given
```
And we can see that the Mac Address is given