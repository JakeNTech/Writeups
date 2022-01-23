# Logs on logs (500)
`What is the logfile sequence number for the file "fruit_Assortment.jpg"`

This challenge had me stupmed for a bit. While I was busy trying to find log file tools and working out how the $logfile worked the answer was staring me in the face! 
I found a tool online, after having spent ages finding out how the $logfile works, called NTFS Log Tracker, which looks really cool!

You give it a $logfile and a $MFT it parses them both to work show you the contents of the log file. The log file is a log of the files (durr) and what happens to them, such as deletion and creation etc. but it only stores so many results, so this is not the answer.

When we start looking at our MFT Dump CSV again there is a column for a Sequence number, something which I hadn't noticed before! and we get the value `1276820064` this is cool that we can get this infoamtion from here!