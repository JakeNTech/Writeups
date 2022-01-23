# MemLabs Lab 4 - Obsession
`My system was recently compromised. The Hacker stole a lot of information but he also deleted a very important file of mine. I have no idea on how to recover it. The only evidence we have, at this point of time is this memory dump. Please help me. Note: This challenge is composed of only 1 flag.`

Once again the dump file is using Windows 7, we can start with `pslist` and only one thing jumps out us is `StikyNot.exe`, which is presumably Windows Destkop stickynotes, so I would guess there is somthing here that may be needed at somepoint. 
The next thing to try is to run `filescan` reading throught the output there are a few intresting items:
```
0x000000003e8ad250     14      0 R--r-- \Device\HarddiskVolume2\Users\eminem\Desktop\galf.jpeg
0x000000003e8d19e0     16      0 R--r-- \Device\HarddiskVolume2\Users\eminem\Desktop\Screenshot1.png
0x000000003e8a85b0      2      0 RW-rw- \Device\HarddiskVolume2\Users\eminem\AppData\Roaming\Microsoft\Windows\Recent\Flag not here.lnk
0x000000003fc398d0     16      0 R--rw- \Device\HarddiskVolume2\Users\SlimShady\Desktop\Important.txt
```
So we can get thease files out of the image:
```bash
$ mkdir images
jakentech@NevilleLongbottomVM:~/Desktop/MemLabs/Lab 4$ volatility -f MemoryDump_Lab4.raw --profile=Win7SP1x64 dumpfiles -Q 0x000000003e8a85b0 --dump-dir ./images
Volatility Foundation Volatility Framework 2.6
DataSectionObject 0x3e8a85b0   None   "\Device\HarddiskVolume2\Users\eminem\AppData\Roaming\Microsoft\Windows\Recent\Flag not here.lnk"
jakentech@NevilleLongbottomVM:~/Desktop/MemLabs/Lab 4$ volatility -f MemoryDump_Lab4.raw --profile=Win7SP1x64 dumpfiles -Q 0x000000003e8d19e0 --dump-dir ./images
Volatility Foundation Volatility Framework 2.6
DataSectionObject 0x3e8d19e0   None   "\Device\HarddiskVolume2\Users\eminem\Desktop\Screenshot1.png"
jakentech@NevilleLongbottomVM:~/Desktop/MemLabs/Lab 4$ volatility -f MemoryDump_Lab4.raw --profile=Win7SP1x64 dumpfiles -Q 0x000000003e8ad250 --dump-dir ./images
Volatility Foundation Volatility Framework 2.6
DataSectionObject 0x3e8ad250   None   "\Device\HarddiskVolume2\Users\eminem\Desktop\galf.jpeg"
jakentech@NevilleLongbottomVM:~/Desktop/MemLabs/Lab 4$ volatility -f MemoryDump_Lab4.raw --profile=Win7SP1x64 dumpfiles -Q 0x000000003fc398d0 --dump-dir ./images
Volatility Foundation Volatility Framework 2.6
DataSectionObject 0x3fc398d0   None   "\Device\HarddiskVolume2\Users\SlimShady\Desktop\Important.txt"
jakentech@NevilleLongbottomVM:~/Desktop/MemLabs/Lab 4$ volatility -f MemoryDump_Lab4.raw --profile=Win7SP1x64 dumpfiles -Q 0x000000003fc398d0 --dump-dir ./
Volatility Foundation Volatility Framework 2.6
DataSectionObject 0x3fc398d0   None   "\Device\HarddiskVolume2\Users\SlimShady\Desktop\Important.txt"
```
Intrestingly the notepad file doesn't seem to want to extract from the dump file! We can come back to this! 

Moving to the images there are two, one is a screenshot showing the google logo (Suggesting we need to look at intrenet history) and the other is the Joker; Running exiftool against them shows nothing out of the ordinary but on the screenshot there is a Warning:
```
Warning                         : [minor] Trailer data after PNG IEND chunk
```
Not too sure if this is normal, but we cna have a look in a hex editor; when we look at it I suspect that there is nothing else to this file as the `IEND` hex is followed by ``.B'`` and a massive load of `0000`; We can always come back if we don't manange to find anything else. 

What about steganography, might be a bit of a long shot but we might as well give it ago:
```
$ steghide extract -sf Screenshot1.png 
Enter passphrase: 
steghide: the file format of the file "Screenshot1.png" is not supported.
jakentech@NevilleLongbottomVM:~/Desktop/MemLabs/Lab 4/images$ steghide extract -sf galf.png 
Enter passphrase: 
wrote extracted data to "LMAO.txt".
jakentech@NevilleLongbottomVM:~/Desktop/MemLabs/Lab 4/images$ cat LMAO.txt 
Move on bro, there is nothing here :)
```
This is intresting as it's either just a red herring or there is more to this that meet's the eye.

Having a bit of reaserch what if the notepad file has been deleted, hence why we can't get it...but what if we can? Well we need to run `mftparser` and see what we can get:
```
$FILE_NAME
Creation                       Modified                       MFT Altered                    Access Date                    Name/Path
------------------------------ ------------------------------ ------------------------------ ------------------------------ ---------
2019-06-27 13:14:13 UTC+0000 2019-06-27 13:14:13 UTC+0000   2019-06-27 13:14:13 UTC+0000   2019-06-27 13:14:13 UTC+0000   Users\SlimShady\Desktop\Important.txt

$OBJECT_ID
Object ID: 7726a550-d498-e911-9cc1-0800275e72bc
Birth Volume ID: 80000000-b800-0000-0000-180000000100
Birth Object ID: 99000000-1800-0000-690d-0a0d0a0d0a6e
Birth Domain ID: 0d0a0d0a-0d0a-6374-0d0a-0d0a0d0a0d0a

$DATA
0000000000: 69 0d 0a 0d 0a 0d 0a 6e 0d 0a 0d 0a 0d 0a 63 74   i......n......ct
0000000010: 0d 0a 0d 0a 0d 0a 0d 0a 66 7b 31 0d 0a 0d 0a 0d   ........f{1.....
0000000020: 0a 5f 69 73 0d 0a 0d 0a 0d 0a 5f 6e 30 74 0d 0a   ._is......_n0t..
0000000030: 0d 0a 0d 0a 0d 0a 5f 45 51 75 34 6c 0d 0a 0d 0a   ......_EQu4l....
0000000040: 0d 0a 0d 0a 5f 37 6f 5f 32 5f 62 55 74 0d 0a 0d   ...._7o_2_bUt...
0000000050: 0a 0d 0a 0d 0a 0d 0a 0d 0a 0d 0a 5f 74 68 31 73   ..........._th1s
0000000060: 5f 64 30 73 33 6e 74 0d 0a 0d 0a 0d 0a 0d 0a 5f   _d0s3nt........_
0000000070: 6d 34 6b 65 0d 0a 0d 0a 0d 0a 5f 73 33 6e 0d 0a   m4ke......_s3n..
0000000080: 0d 0a 0d 0a 0d 0a 73 33 7d 0d 0a 0d 0a 47 6f 6f   ......s3}....Goo
0000000090: 64 20 77 6f 72 6b 20 3a 50                        d.work.:P

***************************************************************************
***************************************************************************
```
We get a lovely hex output of the file, which containes the flag. It would still be intresting to see what was in the stickynote! 