# Interstellar Docking Scene Music (300)
`Name one of the apps that were on this device's dock. Provide them in bundle format: com.provider.appname`

On the SANS FOR585 Poster there is a artifact listed about Homescreen icon layout:
`/private/var/mobile/Libary/SpringBoard/IconState.plist` we can export this as XML and view it in notepad/Sublime:
```
<dict>
	<key>buttonBar</key>
	<array>
		<string>com.apple.MobileSMS</string>
		<string>com.apple.mobilesafari</string>
		<string>com.apple.mobilemail</string>
		<string>com.apple.Music</string>
	</array>
	<key>iconLists</key>
```
So we can chose one from the list!