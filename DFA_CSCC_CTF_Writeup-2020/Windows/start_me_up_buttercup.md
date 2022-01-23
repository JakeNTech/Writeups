# Start me up buttercup (300)
`What cloud service was a Startup item for the user admin?`

For this we need to look at the NTUser.dat for the admin account. So, we open it in registry explorer:\
Looking at the key:\
`NTuser.dat\Software\Microsoft\Windows\CurrentVersion\Run`
and we see:
```
Registry file: F:\Users\admin\NTUSER.DAT
Key: Software\Microsoft\Windows\CurrentVersion\Run
Last write: 2020-04-03 02:14:39
Value: OneDrive (RegSz)
Data: "C:\Users\admin\AppData\Local\Microsoft\OneDrive\OneDrive.exe" /background
Slack: 00-00-00-00-00-00
```
so we know it was OneDrive