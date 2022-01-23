# Hash it real good (50)
`What's the CRC64 hash of the file "fruit_apricot.jpg"?`

The first job here is to locate the file, searching for the name using file explorer showed nothing (Serching with E01 mounted using Arsenal) so insted I opend FTK and mounted the disk image in thair and searched for the same file; the first hit is a file path `c:\Users\hansel.apricot\Pictures\fruit_apricot.jpg` with this infomation we can navigate to this location in explorer, but its not there! It's in the save picture folder insted, odd! The next job is to get the hash, I chose to use the command line and so opened cmd and used the commands, using 7zip after it had been added to the PATH variable: 
```
> 7z h -scrcCRC64 ./fruit_apricot
7-Zip 19.00 (x64) : Copyright (c) 1999-2018 Igor Pavlov : 2019-02-21

Scanning
1 file, 112596 bytes (110 KiB)

CRC64                     Size  Name
---------------- -------------  ------------
ED865AA6DFD756BF        112596  fruit_apricot.jpg
---------------- -------------  ------------
ED865AA6DFD756BF        112596

Size: 112596

CRC64  for data:              ED865AA6DFD756BF

Everything is Ok
```
And the hash is the flag, also can't say I had ever heard of CRC64 before either!