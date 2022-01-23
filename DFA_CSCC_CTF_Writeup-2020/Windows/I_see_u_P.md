# I see u P (400)
`What was the last IP address the machine was connected to?`

The brief of title of this challenge had me puzzled for a while, I originally was thinking about RDP and file server connections but there where RDP logs, nor could I find any FTP related artifacts.
I then thought about a Registry key that records network configurations `SYSTEM\ControlSet001\Services\Tcpip\Parameters\Interfaces\`
Navigating to this key shows three “Interfaces” but it’s likely we only need to look at one of them, (As this image file was made in a Virtual Machine) clicking through them only one of them shows anything useful.
This key contains all sorts of information such as the DHCP server address, Lease time, Gateway and IP address given to the machine from the DHCP server. 
```
| Value Name         | Data          |
|--------------------|---------------|
| DhcpDefualtGateway | 192.168.2.1   |
| DhcpIPAddress      | 192.168.2.242 |
| DhcpServer         | 192.168.2.1   |
```
So lets try thease IP's as the answer, the most likely is going to be the `DhcpIPAddress` and it worked!