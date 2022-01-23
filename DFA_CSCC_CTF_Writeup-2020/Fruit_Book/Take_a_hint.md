# Take a hint (550)
`What's hansel.apricot's password hint?`

This took a fair bit of investigation and a few false leads but we got thair. There is a plist that contains some information about the way that the users can login:
`/private/var/db/dslocal/nodes/users/<short_username>.plist` we can export the plist and then convert it to an XML file but the easy thing to do is view the file in Autopsy:
```
-hint
|- Family Opinion
``` 
and so this is the flag