# FBI Open up (600)

`What is hansel.apricot's Open Directory user UUID? Flag formatted as: flag<XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX>`

When I was originally searching for a lead I could only find ways to get the UUID from a live system using the command line, and as this is a dead system we can't run thease commands, even if we had the disk image mounted to a OS X system. There was also no mention of any files that contain this infomation, although there must be some!\

While I was trying to get mac-apt to work I moved over to a Kali VM to use it there (As python pip is a bit of a handful in WSL!) but one of the modules in mac-apt is UUID! so we can run the tool!\
```
$ python3 mac_apt.py E01 /media/jakentech/DFA_CSCC_CTF/ImageFile/DFA_Mac/FruitBook.E01 ALL -x -O /home/jakentech/Desktop/MAC
```
We examin the XLSX file like we did before, and look at the users sheet:\
```
| Username       | RealName       | Homedir               | UID | UUID                                 |
|----------------|----------------|-----------------------|-----|--------------------------------------|
| hansel.apricot | Hansel Apricot | /Users/hansel.apricot | 501 | 5BB00259-4F58-4FDE-BC67-C2659BA0A5A4 |
```
This table has alot of information on it but it also has the source of where it gains the information from:
`/private/var/db/dslocal/nodes/Default/users/hansel.apricot.plist` and we can look at this to confirm what the tool is saying, as its a plist file its an XML file, so using autopsys application tab on the file, there is a key called `generateduid` which has the value of the UUID mac-apt pulled out!