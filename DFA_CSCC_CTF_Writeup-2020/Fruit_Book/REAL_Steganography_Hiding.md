# REAL Steganography Hiding (600)
`Find the flag in the GoodExample.jpg image. It's hidden with better tools.` 

There are two methods that I can think of to solve this, using the steghide linux command or a decoder online. I chose to use steghide first, after havign exported the file from autopsy and moving it to a Linux VM we can run the command:
```
$ steghide extract -sf ./GoodExample.jpg
Enter passphrase:
wrote extracted data to "steganopayload27635.txt"
$ cat steganopayload27635.txt 
Our latest phone will have flag<helicopter> blades and 6 cameras on it. No
other phone has those features!
```
Thankfully there was no password used and it extracted nicely!