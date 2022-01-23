# Covering Tracks (400)
`What was the file 'Examplesteg.jpg' renamed too?`

Running a search for the file name brings up two files (In autopsy) `windows.plist` and the other being `download.plist` from the "sneaky" user. When looking at the download.plist it would appear that there is a hash assiosated with the file that is downloaded (It turns out this isn't the case or the file being moved effeceted the hash (Which is unlikely)).\
However the `download.plist` shows the size of the file that has been downloded and the file in question was `141705 bytes` so we can look at the suspected files and see if the size matches.\
In `/Users/Shared` there are a number of images, and the one that has the exact same size as `Examplesteg.jpg` is `GoodExample.jpg` so this is the flag!