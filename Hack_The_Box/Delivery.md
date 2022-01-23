# Delivery
```
IP = 10.10.10.222
```
First we nmap `nmap -A -vvv 10.10.10.222 | tee nmap_scan`, we can see two ports are open, 22(SSH) and 80(HTTP).\
When we visit the site we can see two links, one to a HelpDesk and one to a MatterMost server, a chat service. However to gain access to this we need to have a `delivery.htb` email, and we also need to be able to gain access to a conformation link too.\
To get around this we open a ticket on the HelpDesk, once we have created a ticket we get a message telling us that if we want to add things to the ticket we can by emailing `5275830@delivery.htb`, we can take this address and register for a mattermost account.\
When we have created an account we can go back to the ticket and check the status using the email registered to the ticked and the ID from the given email address, once on the status page we can see a post about a successful registration with a link to mattermost. We can follow this link, log in and yay! we are into the internal chat.

Reading the messages on this chat we can see some credentials:
```
Credentials to the server are maildeliverer:Youve_G0t_Mail!
```
We simply SSH into the machine and we have a user.txt waiting for us.\
## Root
To gain access to the root account we can first try running `sudo -l` but we can't run anything. We already know that the password for the root user is likely to be some variation of `PleaseSubscribe!` as seen on the messages in the Mattermost server. Having a bit of a dig around shows us that the `/opt` directory is home to the mattermost install, inhere there is a config file `/opt/mattermost/config/config.json` in this file is some mysql credentials:
```json
"DataSource": "mmuser:Crack_The_MM_Admin_PW@tcp..."
```
This is quite a big hint, so clearly the Mattermost Admin password is the variation of the `PleaseSubscribe!` password. We can login with mysql to get this hash:
```bash
$ mysql -u"mmuser" -p"Crack_The_MM_Admin_PW" mattermost
> show tables;
> select * from Users; #This gives us the column names of the database
> select Password from Users where Username = "root";
$2a$10$VM6EeymRxJ29r8Wjkr8Dtev0O.1STWb4.4ScG.anuu7v0EFJwgjjO 
```
This is a bcrypt hash, we now need to work on the variation part, the chances of it being a huge variation are low se we can start with just two numbers, to make a wordlist of the variations for use with John The Ripper we can use a small python script, adding more if we need too:
```python
password = "PleaseSubscribe!"
for i in range(0,100):
    print(password+str(i))
```
We run this outputting it to a text file so we can use john, we save our hash from the database into a file.
```
$ john --wordlist=./wordlist.txt hash.txt
$ john --show hash.txt
?:PleaseSubscribe!21

1 password hash cracked, 0 left
```
We can then login as the root user. There is a note.txt that has a link to a really interesting blog post too about this method of attack!