# MATCHING WITH '*'
now we need to use '*' to navigate through cd to challenge in less than 4 characters. since we are already in our home directory we will use command cd /ch* to get into th echallenge directory and then run to get the flag
```
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{cJQRLxCDwl5pZXH8E_iUr-3Mh2m.dFjM4QDL5MTM1czW}
```



# MATCHING WITH '?'
here the '?' can represent only a single character. Here we used '?' in place of letters l and e in the word challenge.
```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{0IovPNlYhcdoWpW8eyJBWejfIay.dJjM4QDL5MTM1czW}

```

# MATCHING WITH []

here we first went into /challenge/files then we use the /challenge/run command along with flag_[] command.
the arguments inside the square bracket are used to filter the files.

```
sameeksha03@DESKTOP-965QKSJ:~$  ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ ls file_[absh]
file_a  file_b  file_h  file_s
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{MdKD5JILsBPEyGYrUPzkDm_1Mky.dNjM4QDL5MTM1czW}

```


# MATCHING PATHS WITH []
here we ran the /challenge/run with the absolute path /challenge/files to get the desired files.the arguments inside the square bracket are used to filter the files.


```
sameeksha03@DESKTOP-965QKSJ:~$  ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[absh]
You got it! Here is your flag!
pwn.college{w_WAYF7Rg57sX8wFM6X8I5lrZMk.dRjM4QDL5MTM1czW}
```

# MIXING GLOBS

First we entered into the path then i checked the list of files present inside it using the ls command. Then we finally ran the command /challenge/run along with [] to filter the output.
```
sameeksha03@DESKTOP-965QKSJ:~$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls
amazing      delightful   great       jovial    magical     pwning   splendid   victorious  youthful
beautiful    educational  happy       kind      nice        queenly  thrilling  wonderful   zesty
challenging  fantastic    incredible  laughing  optimistic  radiant  uplifting  xenial
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [epc]*
You got it! Here is your flag!
pwn.college{M-dKxKl0s9IJvh1xnDJlEjNONZ_.dVjM4QDL5MTM1czW}
```


# EXCLUSIONARY GLOBBING
If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed. Here we went into the path /challenge/files and diplayed the output from command /challenge/run which didn't contain 'p','w' and 'n'.

```Connected!
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{Q0XYsLBFDWsyLlRejkoFipNQ0K-.dZjM4QDL5MTM1czW}
```
