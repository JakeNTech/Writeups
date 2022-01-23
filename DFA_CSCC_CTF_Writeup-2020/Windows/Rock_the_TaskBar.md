# Rock the TaskBar (400)
`Which user had the most items pinned to their taskbar? WARNING: You have 1 attempt for this question`

My first thought was what? Does it wasn’t applications that are pinned or files that have been pinned in JumpLists. I’ll start with jump lists as theoretically Custom Jumplists
We can parse each user Custom Jumplists to get a picture as to what applications where pinned to the task bar:
`F:\Users\<user> \AppData\Roaming\Microsoft\Windows\Recent\CustomDestinations`

However, it wasn’t, the user that had the most application jump lists were Tim, but he wasn’t the flag was wrong! But This does not stop me from looking and trying to work it out. It turns out that the NTUSER holds a key that records how many things are pinned and what they are (Kind of)
`Software\Microsoft\Windows\CurrentVersion\Explorer\Taskband`

But it also turns out this is wrong as all the users have the same number of things pinned (9) and this is unlikely.
On even more investigation it turns out the file path:
`%AppData%\Microsoft\Internet Explorer\Quick Launch\User Pinned\TaskBar`
So, time for some more snooping, but just looking in FileExplorer still doesn't show us much!, I tried it on myself and noticed that this location doesn't show Windows Default items.

While solving the Strawberry_SID's challange I decided to have a look, and the user with the most pinned was the Admin user:
```
- Edge
- File Explorer
- Microsft Store
- Mail
- FireFox
```
Nevermind!