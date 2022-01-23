# We've renamed it "Fruit Address" (200)
`Provide the MAC address of the ethernet adapter for this machine`

After some reserch there is a log that will contain the answer to this challange. `/private/var/log/daily.out` 
When we look at the log there is a small section on ethernet:
```
en0   1500  <Link#4>    00:0c:29:c4:65:77   372733     0    73025     0     0
en0   1500  fe80::8c8:8 fe80:4::8c8:87c2:   372733     -    73025     -     -
en0   1500  184.171.151/2 stu-181-151-171   372733     -    73025     -     -
```
and the only thing in this strings dump that looks like a MAC address is `00:0c:29:c4:65:77` so this is the flag. 