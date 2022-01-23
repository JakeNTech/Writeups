# I'm Just Trying to do my iObeSt (50)
`What ios version is this device on?`

After some reserch I found that the iOS version can be found in the `general.log`:
`private/var/logs/AppleSupport/general.log`
The files we are given for this catagory are logical files, rather than an E01 or dd, but we will still use autopsy as at the very least its a convient strings/hex viewer and allows us to more easily preform keyword searches.
Looking at this file we see that:
```
Device Software Diagnostic Log
Version: 3
OS-Version: iPhone OS 9.3.5 (13G36)
Model: iPad3,1
```
There are another couple of lines to this file including the devices Serial Number and the date of creation. But the iOS version is 9.3.5