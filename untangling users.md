# BECOMING ROOT WITH USER
Earlier we used the /challenge/getroot program to become the root user. But Linux installation does not have /challenge/getroot. Instead, there are two utilities used for this purposes: su and sudo.Because it has the SUID bit set, su runs as root.On giving the ``` su``` command it asks for the password which in this case is hack-the-planet.
```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{o8LlTk0ehV1KBZ3jnCPp6SX3aOJ.dVTN0UDL5MTM1czW}
```
