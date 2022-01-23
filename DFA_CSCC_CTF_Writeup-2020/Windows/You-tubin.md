# You-tubin' (100)
`What was the URL for the youtube video watched by Jim?`

So far I have noticed that there are a number of browsers on the system:
-	IE (Comes with W10)
-	Edge (Also comes with IE)
-	TOR
-	FireFox
-	Chrome
(This just answered another challenge Browsing in all the wrong places)
But we can look at the history for Firefox and Chrome first (As its unlikely for someone to use IE and edge with these installed and TOR Is a bit overkill for YouTube).
We can start with Firefox (Mainly as if I start with chrome I get the answer too fast!)
We know we are looking for the history from Jim and the firefox history for them lives under:\
`F:\Users\jim.tomato\AppData\Roaming\Mozilla\Firefox\Profiles\k4sswyli.default-release\places.sqlite`

Scrolling around shows that there is no YouTube links, I also looked on the other tables just in case I was wrong but nothing. Time to move to chrome!
Chrome history in this case is stored in:\
`F:\Users\jim.tomato\AppData\Local\Google\Chrome\User Data\Default\History` This is an SQLite file althought it hasn't got an extention.
But changing tables is where things gets interesting, the visit table houses the ID of the URL’s visited and some other funky information, such as visit duration and it looks like it stores where the user came from too but I can’t remember of the top of my head and I haven’t now got the time to research this (Although that sounds like a project for another day!) We need to look at the URL table:
```
| id | URL                                         | title                                 | visit_count |
|----|---------------------------------------------|---------------------------------------|-------------|
| 12 | https://www.youtube.com/watch?v=Y-CsIqTFEyY | How To Hack Into a Computer - YouTube | 1           |
```
There are alot of other intresting things here but we have the video ID (Which is after the "?v=")