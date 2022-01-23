# Logs on logs pt 2 (150)
`Which user has the most logs ons / how many logons do they have? Answer in the format flag<username/#>`

For this challenge we need to go back and look at SAM:
```
C:\Windows\System32\Config\SAM

SAM\Domains\Account
```
Looking at this file on registary explorer the admin user has 10 logins!