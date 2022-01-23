# Secrets, secrets are no fun (550)
`Jim has some dirt on the company stored in a docx file. Find it, the flag is the fourth secret, in the format of <"The flag is a sentence you put in quotes">.`

The first place to look is to see what docx files jim has been looking at…time to go to registry explorer, and there are three recent word files, with unknow locations:
```
-	Document1.docx
-	CompanySecrets.docx
-	Untitled 1.docx 
```
We navigate to the recent folder in the Recent Documents folder and copy the lnk files out and into a dump folder on the D drive, form there we can run JLECmd; after looking at the CSV file we can see that we are going to be looking at files sotred on the desktop, there is one word document:
```
Nothing to see here
```
so this is not it, There where references to another couple of files (Suggesting that this document has either been re-named or the others have been deleted) Time for some Recycle Bin forensics.\
And so it may be one of these that we need to look at, time for some FTK exporting.\
So the documents named “Documents” are not the correct ones, we need to search! For this I opened autopsy and enterd the name of the file that must contain the company secrets “company secrets” and going through the results it gives us a hit on a folder on Jim’s desktop:\
`Users/jim.tomato/Desktop/Document1/file.xml`\
This is interesting as there are two of these files here, and both have been marked as deleted:

One of them has some intresting information:
```
file.xml Fruit inc. 
company secrets
· Tim is sleeping with his secretary
· Miriam is copying designs from the iPhone
· Suzy was only hired for her looks
· Customer data is not stored securely 
```
When looking at the metadata it gives us a file path for a directory on the Desktop:
`F:\Users\jim.tomato\Desktop\Document1\file.xml` And when looking in autopsy not only are there two of thease files, but autopsy reports the file deleted, but we still have the secret that is needed.