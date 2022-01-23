# Missed connections (150)
`What is the name of the DHCP domain the device was connected to?`

To solve this, we need to look at the network interfaces, so to registry explorer we go:
`SYSTEM\CurrentControl001\Services\Tcpip\Parameters\Interfaces\`

The third sub key contains some good information, including the DHCPdomain which is `fruitinc.xyz`