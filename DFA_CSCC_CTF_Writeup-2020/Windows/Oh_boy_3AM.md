# Oh Boy 3AM (150)
‎`What time did Tim download his background image? Answer in MM/DD/YYYY HH:MM format (UTC).`

The first task is working out what image has been set as the wallpaper and for this we take to registry explorer and open the NTUSER.DAT:
```
NTUSER\ControlPanel\Desktop
```
And we get alot of infomation, the most useful being where the file is stored:
```
C:\Users\tim.apple\Pictures\Saved Pictures\hqdefault.jpg
```
And there is indeed a picture here so now we need to work out when this file was downloaded, and there are couple of ways this can be done, the first it to look at the metadata for this image and see what time it was written/modified:
```
Created:	05 April 2020, 04:49:53
Modified:	05 April 2020, 04:49:54
Accessed:	09 May 2020, 19:46:52
```
The issue with thease time stamps is that it doesn't tell us when it was downloaded. 
But when we consult our SANS poster and file downloads the first thing we see is open/save MRU:
```
NTUSER.dat\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\OpenSavePIDIMUR
```
and when we look at this registary key we see the problem, our windows 10 VM is set to GMT/BST so all Windows time stamps are converted to match. But most forensic applications either don’t touch the time stamps or convert them to UTC(/GMT+0) so the easy solution is to change the time zone of the VM, which I am about to do. The registary key in question only shows when the file was first opened, but highlights the issue with the time stamps. Now the VM has been converted to UTC. 
So now we can be sure that this file was downloaded on the 5-4-2020 03:49:53