# Book it real good (200)
`How many bookmarks are registered in safari? Warning, you only have 1 try at this`

Just looking at what autopsy is spitting out it claims there are 13 bookmarks registred to Safari, however its worth checking the relevent file anyhow.\
Bookmarks for Safari are stored in `/Users/<user>/Libary/Safai/Bookmarks.plist` extracting the information using the Strings view in autopsy we get a list of URL's:
```
apple.com
icloud.com
yahoo.com
bing.com
google.com
wikipedia.com
facebook.com
twitter.com
linkedin.com
weather.com
yelp.com
tripadvisor.com
mail.zoho.com
```
And compearing this to a result from my own MacOS install it looks to be true.(I thought some of them could be defualt ones that even if not shown they could be hidden)\
Taking the time to look at the `Sneky` user showed nothing, they didn't even have this file so it is assumed that they have no bookmarks. So the flag is 13, however I stuffed it up typing it in so I blew my chance :(