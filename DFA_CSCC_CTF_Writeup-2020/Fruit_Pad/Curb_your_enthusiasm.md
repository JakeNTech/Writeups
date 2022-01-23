# Curb your enthusiasm (100)
`What is the title of the webpage that was viewd the most?`

For this we need to locate the safari history, after some searching it appeared to be located at: `private/var/mobile/Containers/Data/Application/<Apple_safari_GUID>/Libary/Safari/History.db` like OS X this file is an SQLite file so examining it there are a number of serches but the one that is most frequently viewd is `Kirby with legs - Google search` so this is the flag. It's worth being sure that the visit counts are accurate (due to re-loads or redirects) but infact thair where mutiple enterys.