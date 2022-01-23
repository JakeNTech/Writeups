# A second listner (50)
`File shell.pcapng What is the port for the second shell?`

We need to go to `Statisctics -> Conversations`, and move to the TCP tab, there we see a fair few converstaions:

Port 80 is always used for HTTP traffic so I am not that interested in those right off the bat, but there is one conversation that lasted significantly longer then the others, we are looking at the TCP tab as that’s the protocol that a remote shell uses, we click on it and press follow stream.
We see it looks like an SSH session, and that the user was trying to pass `/etc/passwd` file onto a listner using port 9999, we can then view this and see the /etc/passwd file.