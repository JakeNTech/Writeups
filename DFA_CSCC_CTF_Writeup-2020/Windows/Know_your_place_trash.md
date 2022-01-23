# Know your place, trash (75)
`Which user has a photo of a dog in their recycling bin? You have two tries for this flag.`

We are going to solve this in two parts, the first is running an Eric Zimmerman tool and the second is by using FTK. First we need to run RBCmd to help parse the files in the recycle bin, as the metadata is speperated from the actual file when it gets allocated to the $Recycle.Bin.
```
> RBCmd -d "F:\$Recycle.Bin" --csv "C:\temp"
RBCmd Version 0.5.0.0
```
Opening FTK we add the image file and start browsing through the recycle bin directorys and there is indeed a picture of a dog 
```
C:
|- $Recycle.Bin
|-- S-1-5-21-2446097003-76624807-2828106174-1005
|--- $IGETTALS.jpg
```
This is a picture of a lovely doggo and in RBCmd we can locate this file and see where it was located on the system before someone hit the delete button:
```
| SourceName                                                                | FileType | FileName                                                  |
|---------------------------------------------------------------------------|----------|-----------------------------------------------------------|
| F:\$Recycle.Bin\S-1-5-21-2446097003-76624807-2828106174-1005\$IGETALS.jpg | $I       | C:\Users\hansel.apricot\Downloads\Chinook-On-White-03.jpg |
```
And it was in Hansel Apricots directory so lets try thair username as the flag. It took it!