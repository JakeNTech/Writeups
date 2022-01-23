# Some good ol fashion txt (50)
`File dns.pcapng What is the response for the lookup for flag.fruitinc.xyz?`

We need to look for the DNS request for `flag.fruitinc.xyz` this isn't too hard as we can just look with out filtering, as there arn't that many items in this capture.
We find the two packets there isn't anything that stands out about the first one, but the responce is intresing:
```
Answers
    flag.fruitinc.xyz: type TXT, class IN
        Name: flag.fruitinc.xyz
        Type: TXT (Text strings) (16)
        Class: IN (0x0001)
        Time to live: 604800 (7 days)
        Data length: 13
        TXT Length: 12
        TXT: ACOOLDNSFLAG
```
So this is what the server responded with the lookup request.