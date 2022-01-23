# Fetch my pre Alfred (350)
`Which Firefox prefetch file has the most runtimes? Flag format is flag<filename/#oftimesrun>`

We first need to navigate to the prefetch directory for the E01, `F:\Windows\Prefetch` and then get a CMD prompt, we could copy out just the FireFox files but we might as well parse all of the items in this directory, incase we need to use it again:
```
> PECmd -d "F:\Windows\Prefetch" --csv "D:\windows\prefetch"
.
.
.
---------- Processed 'F:\Windows\Prefetch\WWAHOST.EXE-776591F6.pf' in 1.49194220 seconds ----------
Processed 217 out of 217 files in 139.3990 seconds

CSV output will be saved to 'D:\Windows\FireFox_Prefetch\20200618150547_PECmd_Output.csv'
CSV time line output will be saved to 'D:\Windows\FireFox_Prefetch\20200618150547_PECmd_Output_Timeline.csv'
```
Once this command has run (It takes awhile due to the large number of files involved) we can open the CSV file and filter for firefox:
```
| SourceFilename                              | ExecutableName | RunCount |
|---------------------------------------------|----------------|----------|
| F:\Windows\Prefetch\FIREFOX.EXE-20153F0F.pf | FIREFOX.EXE    | 10       |
| F:\Windows\Prefetch\FIREFOX.EXE-A606B53C.pf | FIREFOX.EXE    | 21       |
| F:\Windows\Prefetch\FIREFOX.EXE-B4420372.pf | FIREFOX.EXE    | 4        |
```
And we can get the flag from this information, the prefetch stores a tonne of other information, including a couple of previous run times/dates. 