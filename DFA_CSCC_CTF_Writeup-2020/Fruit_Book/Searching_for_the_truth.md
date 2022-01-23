# Searching for the truth (600)
`What was exactly typed in the Spotlight searchbar on 4/20/2020 02:09:48?`

This challenge took some digging around, I found myself on a blog that Kevin Ripa had recommended back at Elite LND ’19, https://www.mac4n6.com/blog/2017/7/19/script-update-mac-mru-parser-spotlight-shortcuts-blob-parsing \
This particular page of interest as it shows a python tool for looking at the history, however after spending ages trying to get it to work I ran the help command and got a list of really interesting files:
```
Spotlight Shortcuts - /Users/<username>/Library/Application Support/com.apple.spotlight.Shortcuts
```
This is the only reference to spotlight and as this pyton script was refusing to play nice in WSL we can look at this file without parsing it.
Loading it in autopsy it looks like an XML file (When using strings):
```
	<dict>
		<key>DISPLAY_NAME</key>
		<string>Keychain Access</string>
		<key>LAST_USED</key>
		<date>2020-04-20T00:57:28Z</date>
		<key>URL</key>
		<string>/System/Applications/Utilities/Keychain Access.app</string>
	</dict>
	<key>terminal</key>
	<dict>
		<key>DISPLAY_NAME</key>
		<string>Terminal</string>
		<key>LAST_USED</key>
		<date>2020-04-20T01:27:45Z</date>
		<key>URL</key>
		<string>/System/Applications/Utilities/Terminal.app</string>
	</dict>
```
Neither of thease times match (This is from Hansel's files), so what about "sneaky":
```
	<key>silent</key>
	<dict>
		<key>DISPLAY_NAME</key>
		<string>silenteye-0.4.1b-snowleopard_installer</string>
		<key>LAST_USED</key>
		<date>2020-04-20T02:44:27Z</date>
		<key>URL</key>
		<string>/Applications/silenteye-0.4.1b-snowleopard_installer.app</string>
	</dict>
	<key>term</key>
	<dict>
		<key>DISPLAY_NAME</key>
		<string>Terminal</string>
		<key>LAST_USED</key>
		<date>2020-04-20T02:09:48Z</date>
		<key>URL</key>
		<string>/System/Applications/Utilities/Terminal.app</string>
	</dict>
```
And so they searched for `term` at the time given to us, so this is the flag! Also really intresting to see that OSX logs thease searches, as I can't think of a reason it would need too!