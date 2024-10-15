# BECOMING ROOT WITH USER
Earlier we used the /challenge/getroot program to become the root user. But Linux installation does not have /challenge/getroot. Instead, there are two utilities used for this purposes: su and sudo.Because it has the SUID bit set, su runs as root.On giving the ``` su``` command it asks for the password which in this case is hack-the-planet.
```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{o8LlTk0ehV1KBZ3jnCPp6SX3aOJ.dVTN0UDL5MTM1czW}
```


# OTHER USERS WITH SU

Here when we give arguments along with ``` su ``` command instead to switching to root user it switches to the user which is provided as an argument, which in this case is zardus next we provide the password as mentioned and run the /challenge/run command to get the flag.

```
Connected!
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{0cDiYQvJvX6WNVOW9-iaSZkm3Wr.dZTN0UDL5MTM1czW}
```

# CRACKING PASSWORDS

In this challenge we learnt how to crack the password which might have gotten leaked. For example, backups are often stored, unencrypted and insufficiently protected, on file servers, and this has led to countless data disclosures. Here we try to get the password using the ``` john ``` command . Next we entered the password and ran the /challenge/run command to get the flag.

```
hacker@users~cracking-passwords:~$  john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04764g/s 277.4p/s 277.4c/s 277.4C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{oWL6bUpJphhkJTuvbv96Hcr4_Sn.ddTN0UDL5MTM1czW}
```

# USING SUDO

```
sameeksha03@DESKTOP-965QKSJ:~$  ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@users~using-sudo:~$ sudo hacker
sudo: hacker: command not found
hacker@users~using-sudo:~$ sudo grep pwn.college /flag
pwn.college{g-snXHw1abs5K7i5CsvFxzM5rcQ.dhTN0UDL5MTM1czW}
```
