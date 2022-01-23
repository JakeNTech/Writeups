# Build me up buttercup (50)
`What is the current build number on the system?`

Using Arsenal image mounter to mount the E01 and then using registry Explorer, we need to open the SOFTWARE hive `F:\Windows\System32\Config\SOFTWARE` and then navigating to: `Microsoft\WindowsNT\Current version` we see:
```
| Value Name         | Value Type | Data  |
|--------------------|------------|-------|
| CurrentBuild       | RegSz      | 16229 |
| CurrentBuildNumber | RegSz      | 16229 |
```
so 16229 is the flag