# Black Tuesday

`We received this memory dump from our client recently. Someone accessed his system when he was not there and he found some rather strange files being accessed. Find those files and they might be useful. I quote his exact statement, The names were not readable. They were composed of alphabets and numbers but I wasn't able to make out what exactly it was. Also, he noticed his most loved application that he always used crashed every time he ran it. Was it a virus? Note-1: This challenge is composed of 3 flags. Note-2: There was a small mistake when making this challenge. If you find any string which has the string "**_L4B_3_D0n3_!!**" in it, please change it to "**_L4B_5_D0n3_!!**" and then proceed. Note-3: You'll get the stage 2 flag only when you have the stage 1 flag.`

## Stage 1
The first thing we want to run is `pslist` to see what we might be dealing with, there where a couple of intresting items:
```
0xfffffa8000f97a20 WinRAR.exe             2924   1580      6      210      2      0 2019-12-20 03:47:13 UTC+0000                                 
0xfffffa8000efbb30 WerFault.exe            780   2632      7      160      2      1 2019-12-20 03:48:01 UTC+0000                                 
0xfffffa8000f02b30 NOTEPAD.EXE            2056   1580      1      226 ------      1 2019-12-20 03:48:15 UTC+0000                                 
0xfffffa8000f05b30 WerFault.exe           2168   2632      7  1572864 ------      1 2019-12-20 03:48:15 UTC+0000
```
WerFault.exe is Windows Error reporting so we might find some useful logs. Starting with `crashinfo` fails, as this is an entire memory capture rather then a capture that windows dumped when it crashed. So we can start to look at other things; Consoles, cmdline and cmdscan show nothing of intrest. 
Turning attention to `filescan` and `iehistory` we do see some intresting results:
```
*************************************************
Process: 1580 explorer.exe
Cache type "URL " at 0x2ab6d80
Record length: 0x100
Location: Visited: SmartNet@file:///C:/Users/SmartNet/Secrets/Hidden.kdbx
Last modified: 2019-12-14 10:26:25 UTC+0000
Last accessed: 2019-12-14 10:26:25 UTC+0000
File Offset: 0x100, Data Offset: 0x0, Data Length: 0xa8
**************************************************
Process: 1580 explorer.exe
Cache type "URL " at 0x2ab6e80
Record length: 0x100
Location: Visited: SmartNet@file:///C:/Users/SmartNet/Documents/SW1wb3J0YW50.rar
Last modified: 2019-12-19 13:25:57 UTC+0000
Last accessed: 2019-12-19 13:25:57 UTC+0000
File Offset: 0x100, Data Offset: 0x0, Data Length: 0xb0
**************************************************
Process: 1580 explorer.exe
Cache type "URL " at 0x2ab6f80
Record length: 0x100
Location: Visited: SmartNet@file:///C:/Users/SmartNet/SW1wb3J0YW50.rar
Last modified: 2019-12-19 11:07:52 UTC+0000
Last accessed: 2019-12-19 11:07:52 UTC+0000
File Offset: 0x100, Data Offset: 0x0, Data Length: 0xa8
**************************************************
Process: 1580 explorer.exe
Cache type "URL " at 0x2ab6a80
Record length: 0x100
Location: Visited: SmartNet@file:///C:/Users/SmartNet/Desktop/st4G3$$1.txt
Last modified: 2019-12-11 09:02:13 UTC+0000
Last accessed: 2019-12-11 09:02:13 UTC+0000
File Offset: 0x100, Data Offset: 0x0, Data Length: 0xac
**************************************************
Process: 1396 explorer.exe
Cache type "URL " at 0x2955200
Record length: 0x100
Location: :2019122020191221: Alissa Simpson@file:///C:/Users/Alissa%20Simpson/Pictures/ZmxhZ3shIV93M0xMX2QwbjNfU3Q0ZzMtMV8wZl9MNEJfNV9EMG4zXyEhfQ.bmp
Last modified: 2019-12-20 09:16:09 UTC+0000
Last accessed: 2019-12-20 03:46:09 UTC+0000
File Offset: 0x100, Data Offset: 0x0, Data Length: 0x0
**************************************************
Process: 1396 explorer.exe
Cache type "DEST" at 0x635910f
Last modified: 2019-12-20 09:16:37 UTC+0000
Last accessed: 2019-12-20 03:46:38 UTC+0000
URL: Alissa Simpson@file:///C:/Windows/AppPatch/ZmxhZ3shIV93M0xMX2QwbjNfU3Q0ZzMtMV8wZl9MNEJfNV9EMG4zXyEhfQ.bmp
```
The last item is very intresting as its a Bitmap image storef in a System folder and has an odd name, time to open cyber chef (Although it looks like base64):
```
flag{!!_w3LL_d0n3_St4g3-1_0f_L4B_5_D0n3_!!}
```
So this was a suspicous looking file, but what was in the image, only one way to find out, unfortunatly there is no results for this from the `filescan` :(
## Stage 2
The filename `SW1wb3J0YW50` is also base64 for `important` suggesting that this file may be of intrest to us, we pull out the RAR file and it asks for a password, this seems simlar to another lab, there is also a kdbx file again which is not found in the output from the files command. When running binwalk on the RAR file we don't see the same output as we did for lab2:
```
$ binwalk file.None.0xfffffa80010b44f0.dat 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             RAR archive data, version 5.x
```
It contains a file called Stage 2 so I would guess that we are on the right path. As a random thought I tried using the flag from the first stage as the flag, as the description mentions you will only get the stage 2 flag when you have done the first flag. Amazingly it worked, I was expecting to have to try to ge the contents of the bitmap when I read over the desciption.
![](images/Stage2.png)