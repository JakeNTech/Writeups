# Mmmm, red and DeliciOuS (50)
`What version of MacOS is running on this image?`

After having a google around we found a file path to the location of a file that contains the OS X verion number:\
`System/Libary/CoreServices/SystemVersion.plist`
As I don't have a Macbook that is capable of doing any intense work (A1432) I used a Windows 10 VM and Autopsy to look that the files that where contained within the E01 provided.\
However looking for this folder in the same directory/volume as all the user data drew nothing, as this is sotored in a diffrent volume on the same APFS pool:
```
-Fruitbook.E01
|-Vol_1 (Unallocated)
|-Vol_4 (EFI System Partition)
|-Vol_5 (Unknown)
|--APFS Pool
|---Vol_0 (macOS Catalina - Data)
|---Vol_1 (Preboot)
|---Vol_2 (Recovery)
|---Vol_3 (VM)
|---Vol_4 (macOS Catalina)
|---Vol_5 (Unallocated)
|-Vol_6 (Unallocated)
```
After having located the file at:
```
Vol_5/APFS_Pool/Vol_4/System/Libary/CoreServices/SystemVersion.plist
```
We find that:
```
<dict>
	<key>ProductBuildVersion</key>
	<string>19A583</string>
	<key>ProductCopyright</key>
	<string>1983-2019 Apple Inc.</string>
	<key>ProductName</key>
	<string>Mac OS X</string>
	<key>ProductUserVisibleVersion</key>
	<string>10.15</string>
	<key>ProductVersion</key>
	<string>10.15</string>
	<key>iOSSupportVersion</key>
	<string>13.0</string>
</dict>
```
And so we know that the system was running OS X 10.15 which is Catalina!