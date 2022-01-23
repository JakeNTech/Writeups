# An Apple a day keeps the docx away (200)
`When was the last time a docx file was opened on the device? Answer in UTC, YYYY-MM-DD HH:MM:SS`

The first place I thought of looking was office log files, but this system doens't have Microsoft Office installed; So insted we can look at the NTUSER.DAT for every user and find out this information that way.

Jim has a couple of docx files in his recent docs: and the only one with a timestamp is 2020-04-11 23:23:36\
Miriam Does not have any docx files.\
Suzy Strawberry also doesn’t have any docx files in NTUser.dat\\
Tim Apple does not have any docx file in NTuser.dat either. The admin account doesn’t either. So the last docx document that was open was at `2020-04-11 23:23:36` but we need to work out what time zone this was recorded in to convert to UTC. So we navigate to:
`SYSTEM\ControlSet001\Control\TimeZoneInfomation`\
And we see that the system uses PST so we need to convert from PST to UTC. \
Which gives us:
`2020-04-11 06:23:36` however this is incorrect as the flag but `2020-04-11 23:23:36` is correct, therefor I assume that Eric Zimmernams tool converts time stamps into UTC for us, which is very nice! (After this I did change the time zone on my VM to UTC as I thought I had but clearly didn't)