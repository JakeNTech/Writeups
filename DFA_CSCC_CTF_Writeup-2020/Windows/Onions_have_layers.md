# Onions have layers (150)
`How many times did Jim launch the Tor Browser? You have two attempts at this flag.`

There are a number of ways that we could get the answer for this, the first place to startwas the RecentApps registary key `SOFTWARE\Microsoft\Windows\CurrentVersion\Search\RecentApps`\
There are two references to Firefox that are not in the Program Files (Which would indicate it to be TOR) and adding it up there are 3 RunCounts (As it looks like the install was moved) but this is wrong. So, we can turn to JumpLists, but automatic ones rather than Custom to see if that throws anything up.\
Unfortunately there is nothing in the Jump lists relating to Firefox or TOR but after a look at a SANS poster we could look at the SRUM database, and once we got a new copy of srum_dump, using a tool called SRUM_DUMP 2.0; And we are presented with a huge CSV file for analysis, but we move to the Application Resource Usage tab, and turn that into a table, we can apply the a TOR filter to the application column.\
While there are a couple of results for Firefox/Tor we have a new problem, the SRUM file only stores information for 60 minutes.\
So that was all a few days ago and now I have just had a go with KAPE! One of the options that I had selected was Prefetch, so it ran Eric Zimmerman’s PECmd tool for us (Very nice!)\
The KAPE tool didn’t really do much for us, as prefetch didn’t have anything useful in it, we know that the tor browser has multiple parts to it; firefox.exe and tor.exe:

And TOR was run once but firefox was run 4 times, this is because prefetch isn’t user specific, but there is another registry key that can help us out:
`Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\{CEBFF5CD-ACE2-4F4F-9178-9926F41749EA}\Count`\
The UserAssist key tracks recent usage too, we can see that the firefox.exe that is associated with the TOR install and we can see that `C:\Program1\Browser\forefox.exe` and it was run twice. This is the flag. Its worth noting that we did see this when looking at recentApps.