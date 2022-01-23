# It's time for mail (450)
`How much time was spent on mail.zoho.com on 4/20/2020? Answer in flag<MM:SS>?`

Using a tool called mac-apt, https://github.com/ydkhatri/mac_apt ; running the python script and using the all options:
`python3 mac_apt.py E01 /media/jakentech/DFA_CSCC_CTF/ImageFile/DFA_Mac/FruitBook.E01 ALL -x -O /home/jakentech/Desktop/MAC`\
Using -x pushes the results to a xlsx file, which makes it easier to look at. Looking at the resulting file there is a `ScreenTab`, we can filter this to only show resutls for `mail.zoho.com` and there are 4 reults but only two fall on the date in question:
```
| Application   | Total Time | Start Date |
|---------------|------------|------------|
| mail.zoho.com | 00:01:07   | 2020-04-12 |
| mail.zoho.com | 00:00:30   | 2020-04-12 |
| mail.zoho.com | 00:04:34   | 2020-04-20 |
| mail.zoho.com | 00:16:24   | 2020-04-20 |
```
Adding the two times up for the 20th gives us:\
`00:20:58` so formatting this gives us the flag!