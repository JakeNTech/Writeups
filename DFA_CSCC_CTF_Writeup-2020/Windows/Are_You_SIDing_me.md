# Are you SIDing me??? (100)
`What is the SID of the machine?`

This was a bit complex, the only way that I could find you could get this infomation is via a powershell program; ALthough it's stored on a registary key its encoded and can't be viewed in strings or hex (apparantly). So I deciced to mount the E01 as a VDI run the command and then do a string search for the ouptut just to see if there was any other place it was stored on the system. I opened Kali and ran the command:
```
$ sudo xmount --in ewf /media/sansforensics/DFA_CSCC_CTF/ImageFile/DFA_Windows/DFA_SP2020_Windows.E?? --cache /tmp/disk.cache --out vdi /mnt/windows_mount

$ virtualbox
```
Once virtualbox has oppened we can create a virtual machine using the VDI we have made as a disk rather then creating one. We then hit start, but there is a problem, we don't know the passwords to any of the accounts, and the hits don't help us. So we need to change the passwords. We need to force the machine in to automatic repair; as soon as the machine starts to boot we turn it off until we see `Diagnosing your PC` then we `Troubleshoot -> Advance Options -> Command promt` the next step is to navigate to the OS and the drive the command promt opens on it X: 
```
X:\windows\system32>c:
C:\> dir
``` 
and we see that the list of files isn't right so we need to find the correct volume, and it turnd out it was `D:\` and we need to move into the system32 dirctory
```
C:\>d:

> cd windows/system32

>rename utilman.exe utilman.bak

>copy cmd.exe utilman.exe
```
This copys the command line excecutable and renames it so that it would appeare to be the accessability options exe on the login screen. 
We can then exit this but there is one more step:
```
Troubleshoot -> Advanced options -> Startup settings

Restart

8) Disable early launch anti-malware protection
```
Windows 10 then boots as normal, once we have got to the login screen we press the user accessability button and we end up with a CMD shell
```
> net user

User accounts for \\
---------------------------------------------
admin				Administrator		DefualtAccount
Gues				hansel.apricot 		jim.tomarto
miriam.grapes 		suzy.strawberry 	tim.apple
WDAGUtilityAccount	
The command completed with one or more errors.

> net user admin admin
The command compleated successfully
```
We then need to use this to change the passowrds of the accounts, the command `net user` lists all the users and to change the passwords we use `net user <username> <new_password>`
(Thanks https://www.ghacks.net/2019/01/07/how-to-reset-windows-10-account-passwords/ for the help.)
And we are in! The next thing to do is to get the SID! For this I got the sysinternals psgetsid tool and ran it:
```
S-1-5-21-2446097003-76624807-2828106174
```
This is the flag. But I wasn't happy that that was the only way to find this, it seems overly complicated; So I ran a string serch in autopsy to see if its stored anywere else, after some investigation its stored in the SAM file:
```
SAM\Domains\Bulitin\Aliases\Members\
```
And we do see the SID, as the name of the folder\key still we know for next time!