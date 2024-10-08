# matching with *
now we need to use '*' to navigate through cd to challenge in less than 4 characters. since we are already in our home directory we will use command cd /ch* to get into th echallenge directory and then run to get the flag

hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{cJQRLxCDwl5pZXH8E_iUr-3Mh2m.dFjM4QDL5MTM1czW}




# matching with '?'
here the '?' can represent only a single character.

hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{0IovPNlYhcdoWpW8eyJBWejfIay.dJjM4QDL5MTM1czW}



# matching with []
here we first went into /challenge/files then we use the /challenge/run command along with flag_[] command.


sameeksha03@DESKTOP-965QKSJ:~$  ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ ls file_[absh]
file_a  file_b  file_h  file_s
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{MdKD5JILsBPEyGYrUPzkDm_1Mky.dNjM4QDL5MTM1czW}




# matching paths with []

sameeksha03@DESKTOP-965QKSJ:~$  ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[absh]
You got it! Here is your flag!
pwn.college{w_WAYF7Rg57sX8wFM6X8I5lrZMk.dRjM4QDL5MTM1czW}


# mixing globs

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
