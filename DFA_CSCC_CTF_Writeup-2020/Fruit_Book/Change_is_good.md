# Change is good (600)
`The main file that stores Hansel's iMessages had a few permissions changes. How many times did the permissions change? Warning, you only have 1 attempt at this`\
The only mention to this kind of information online that I could find was to do with FsEvents, and as we have already run mac-apt it helpfully parses thease files for us. There are so many of them they actually get put into two sheets so we need to look at both of them. 
The next step is find out where the iMessages are stored:
`Users/<username>/Libary/Messages/chat.db`\
Filtering both sheets,for that file path, crashed Excel so just hold tight...It will get there...eventually! As there are results on both sheets they can be coppied out into a blank workbook to make it easier, we are also only intrested in resuts that that have the EventFlag `PermissionChange` , and there are 7 changes. 