# Let me in LET ME INNNNNN (200)
`What ap was used to jailbrake this device?`

I ran a keyword serch for `jailbreak`, there where are a number of results including a artifact pointing to a github page:
```
URL : https://nguyenthanh1995.github.io/jailbreak-tool
Date Accessed : 2020-04-13 01:20:08 BST
Referrer URL :
Title :
Program Name : Safari
Domain : nguyenthanh1995.github.io
Username :
```
looking at this website there are a number of jail breaking tools, but as we know we are on iOS 9 there are two "compatiable" apps listed here: `Pangu Jailbreak & Phoenix Jailbreak`.
After having a look on a SANS poster there was a tool that I decided to a play with can list installed applications: https://github.com/abrignoni/iLEAPP:
```
$ python3 ileapp.py -t fs -i /media/jakentech/DFA_CSCC_CTF/ImageFile/DFA_iPad/iPad -o /home/jakentech/Desktop/iOS
```
This particualr script gathers information and collates them into a file structure and shows them in HTML files, rather than XLSX or CSV, however there is a folder for installed apps, when opening the file we can see the bundle ID, path and the sandbox path:
```
| Bundle ID                            | Bundle Path                                                                                 |
|--------------------------------------|---------------------------------------------------------------------------------------------|
| com.saurik.Cydia                     | /Applications/Cydia.app                                                                     |
| com.VN337S8MSJ.supplies.wall.phoenix | /private/var/containers/Bundle/Application/E9DB300B-6B96-422E-9122-327F475623F0/Phoenix.app |
```
(Sandbox path has been removed to make the table fit on one page) and the only two apps that are related to Jailbreaking are Phoneix and Cydia. Cydia is a "marketplace" like application to install mods/tweaks but Phoenix is the app used to Jailbreak, and we know this from the Web artifact earlier. It's possiable that this app was just installed rather then one used to jailbreak but there are no others installed. So Phoenix is the flag!