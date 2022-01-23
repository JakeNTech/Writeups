# I did not start this conversation but I’m ending it! (100)
`What was the last used username? You have three tries for this flag.`

This challange breief could be interpreted to mean a couple of diffrent things, last user name used in a web browser/logon page, last person to be mentioned in a slack chat or the last person loged on; I assumed it to mean last person to logon.

We need to look at the Security Event logs `F:\Windows\System\winevt\Logs\Security.evtx` there are a number of ways that this could be opened, just using the built in event log viewer, an Eric Zimmerman tool or EvenLogExplorer. What ever way you chose to use we need to filter for logon and log off events:
```
4625 - Failed Logon
4624 - Logon
4647 - Logoff
```
While the last log on was miriam grapes the last logon and log-off event's are from Jim Tomato, which makes sence as it goes back to the challange name `But I'm ending it` so was good fun!