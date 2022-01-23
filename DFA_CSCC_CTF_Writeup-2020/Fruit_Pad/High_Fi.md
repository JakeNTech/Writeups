# High Fi! (150)
`What is the name of the Wi-Fi network this device is connected to?`

For this we need to find the Wi-Fi connections for this we need to look at: `/private/var/preferences/SystemConfiguration/com.apple.wifi.plist` we can export this file as a XML file using autopsy and we can see that:
```
<key>BSSID</key>
			<string>5a:7d:7f:3b:c7:d2</string>
			<key>SSID</key>
			<data>
				YmxhY2sgbGFi
			</data>

```
The data feild here shows the SSID but clearly this isnt the SSID, but putting it through the magic module on Cyber Chef shows that is Base 64 encoded and reveals the name `black lab` we we scroll a bit furtherdown in the XML file however we get given the SSID in plain text:
```
<key>SSID_STR</key>
			<string>black lab</string>
```
Confirming that the SSID is `black lab`