# Simple Secret Messaging (150)
`What "copetitive advatge" did Hansel lie about in the file AnotherExample.jpg? Flag will be found in this format: <"two words">. (sumbit as 'flag<"two words">' no single quotes)`\
The way to start this challange is to go snooping arround the files stored on the Vol_5/APFS_Pool/Vol_0 we see that the shared folder is being used, proberbly to share files between the two user accounts on the system. In this directory there are couple of intresting files:
```
- Vol_5/APFS_Pool/Vol_0/Users/Shared
|--secret
|--GoodExample.jpg
|--Example.jpg
|--AnotherExample.jpg
```
There are a number of other files but they are either system files or directorys that appear empty. Looking at AnotherExample there would appear nothing is out of the ordinary, but when we read the secret file:
```
!Our newest phone will have helicopter blades and six cameras and <"flip phone"> technology!
```
And formated nicely is the flag.