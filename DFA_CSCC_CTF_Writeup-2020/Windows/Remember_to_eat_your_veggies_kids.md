# Remember to eat your veggies kids! (75)
`What type of file is "vegtable"? Provied the extention. You have three tries for this flag`

The first thing we need to do is find the file, it appeared in `F:\Users\miriam.grapes\Pictures` so we have two options now, use a command line program called Binwalk or look at the hex header, we shall use binwalk incase there are more than one file in here!
```
$ binwalk ./vegtable

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             7-zip archive data, version 0.4
62021         0xF245          JPEG image data, JFIF standard 1.01
```
So there are two files, a 7z archive and a JPG. The flag is 7z, so the JPEG is either inside the 7z archive or a false lead.