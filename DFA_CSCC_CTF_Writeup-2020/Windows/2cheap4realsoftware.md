# 2cheap4realsoftware (150) - UNSOLVED
`Which user installed LibreCAD on the system? (You have three tries at this flag)`

We can find the installed in Miram's download folder doesn't mean it her who installed it. There are a couple of places that we could find this informaiton:
- SCRUM
- Event Logs
- BAM/DAM

We can start with SCRUM, after having parsed this for another challange we see that the only entery that's in here for the installer and the SID that there is a result for is the Admin user, which makes sence too, but it did not take admin as the flag (I probably spelt it wrong!) but its best to look else where too, but we have a good idea that it will be the admin. 
We can use event logs, and event log explorer:
```
C:\Windows\System32\winevt\Logs\Application.evtx
```
And we need to filter by event log ID 11707, but the only log is for LibreOffice not LibreCAD. There is anther ID that we can try: 1040 but once again there is a pointer to LibreOffice but not LibreCAD.

There isn’t a match. 
There is one last way that I can think of looking, BAM/DAM! (Windows Background Activity Monitor), this is stored in the SYSTEM registry key:
```
F:\Windows\System32\config\SYSTEM: ControlSet001\Services\bam\UserSettings\
```
Now we have this we need to have a look to see who has run anything to do with LibreOffice excecutables, and there is one for LibreCAD and the SID assosiated with this is 1001 and this is the SID that matched admin. 

In the other users there is no mention of this file. I am convinced it was the admin user who ran this despite being in Miriam’s folder.
The answer isn’t admin though! I don’t understand this anymore!

Unless I mistyped admin too many times, which is possiable, but I don't know how else we could find the answer to this. 