# Run forest Run (450)
`What was the last run date of the executable with a MFT record number of 164885? Date format: MM/DD/YYYY HH:MM:SS (UTC).`

The first thing that we need to do is extract the `$MFT` file and for this I chose to use FTK and place it in a tempory folder, and then we can use another Eric Zimmerman tool, MFTECmd:
```
> MFTECmd -f "D:\MFTDump\$MFT" --csv "D:\MFTDump"
MFTECmd version 0.5.0.0
```
And we can open the CSV file and search for this record number, and it comes back to `7zG.exe` and while it does indeed record time stamps for last accessed and created, we have our big prefetch file done, so we can cross reference to that, and we get the time `2020-04-12 02:32:09` just formatting it match what the challange is after and we get the answer, intrestingly this timestamp doesn't match any of those found in the $MFT for this file! intresting! 