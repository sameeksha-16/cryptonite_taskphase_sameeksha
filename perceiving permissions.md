# CHANGING FILE OWNERSHIP
Every file is owned by an individual or a group of individuals. And there are some files which can't be accessed by everyone. So in order to access the files we can change the the user from root using the ```chown``` command.
The syntax is ``` chown user filename ```.

```Connected!
hacker@permissions~changing-file-ownership:~$ ls -l
total 44
-rw-r--r-- 1 hacker hacker    4 Oct  8 13:41 COLLEGE
-rw-r--r-- 1 hacker hacker    1 Oct 12 13:30 PWN
drwxr-xr-x 2 hacker hacker 4096 Oct  6 08:46 a
drwxr-xr-x 2 hacker hacker 4096 Oct  3 08:28 cryptos
-rw-r--r-- 1 hacker hacker    0 Oct  8 19:00 error
-rw-r--r-- 1 hacker hacker  757 Oct  8 14:27 errors.log
-rw-r--r-- 1 hacker hacker   58 Oct  6 07:36 f
-rw-r--r-- 1 hacker hacker  829 Oct  8 14:31 instructions
-rw-r--r-- 1 hacker hacker   58 Oct  6 07:39 m
-rw-r--r-- 1 hacker hacker   93 Oct  8 14:31 myflag
lrwxrwxrwx 1 hacker hacker    5 Oct  6 15:44 not-the-flag -> /flag
-rw-r--r-- 1 root   hacker    0 Oct  8 19:37 open
drwxr-xr-x 2 hacker hacker 4096 Oct  6 07:10 sam
-rw-r--r-- 1 hacker hacker  435 Oct  8 14:14 the-flag
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{EJcigy0_zKPofVH2Nqx0hxkFbnC.dFTM2QDL5MTM1czW}
```


# GROUPS AND FILES

```
Connected!
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ ls -l
total 44
-rw-r--r-- 1 hacker hacker    4 Oct  8 13:41 COLLEGE
-rw-r--r-- 1 hacker hacker    1 Oct 12 13:30 PWN
drwxr-xr-x 2 hacker hacker 4096 Oct  6 08:46 a
drwxr-xr-x 2 hacker hacker 4096 Oct  3 08:28 cryptos
-rw-r--r-- 1 hacker hacker    0 Oct  8 19:00 error
-rw-r--r-- 1 hacker hacker  757 Oct  8 14:27 errors.log
-rw-r--r-- 1 hacker hacker   58 Oct  6 07:36 f
-rw-r--r-- 1 hacker hacker  829 Oct  8 14:31 instructions
-rw-r--r-- 1 hacker hacker   58 Oct  6 07:39 m
-rw-r--r-- 1 hacker hacker   93 Oct  8 14:31 myflag
lrwxrwxrwx 1 hacker hacker    5 Oct  6 15:44 not-the-flag -> /flag
-rw-r--r-- 1 hacker hacker    0 Oct  8 19:37 open
drwxr-xr-x 2 hacker hacker 4096 Oct  6 07:10 sam
-rw-r--r-- 1 hacker hacker  435 Oct  8 14:14 the-flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{ABfryn-UgocLMBbFkF8LIRSmHj7.dFzNyUDL5MTM1czW}
```

# FUN WITH GROUP NAMES
In this challenge our username that is hacker wasn't present in the usual group that is hacker so firat we found our grpname using the ``` id ``` command. Next we used the ``` chgrp ``` command to change the group name and then we ran the /flag command to get the flag.

```
Connected!
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp18283) groups=1000(grp18283)
hacker@permissions~fun-with-groups-names:~$ chgrp grp18283 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{snBEWSc1rDYv3WPBkAHrC5alm2G.dJzNyUDL5MTM1czW}
```

# CHANGING PERMISSIONS

In this challenge, we learnt how to change permissions related to files, as a user,group or as other users. This can be done using the ``` chmod``` command along with mentioning who +/- what has to be changed . Under who we mention who's permission has to be changed and under what we mention what permissions need to be given.

```
sameeksha03@DESKTOP-965QKSJ:~$  ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@permissions~changing-permissions:~$ chmod g+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{cw1PJws1zl_X9QK6Zy062v4LPur.dNzNyUDL5MTM1czW}
```

# EXECUETABLE FILES

In this challenge we changed the permission of /challenge/run of user to executable form so that we will are able to run the command and get the flag . For this we used the ```chmod``` command along with ```u+x``` to change the permissions.
```
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r-xr-x 1 hacker hacker 32 Jul  4 06:37 /challenge/run
hacker@permissions~executable-files:~$ chmod u+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{QZclkr1dOxmULFfEqncBg0S2lai.dJTM2QDL5MTM1czW}
```

# PERMISSION TWEAKING PRACTICE

```
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 0 (of 8)!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-r--rwx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+wx /challenge/pwn
You set the correct permissions!
Round 1 (of 8)!

Current permissions of "/challenge/pwn": rw-r--rwx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ---r----x
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod uo-rw /challenge/pwn
You set the correct permissions!
Round 2 (of 8)!

Current permissions of "/challenge/pwn": ---r----x
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rwxr--rwx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod uo+rwx /challenge/pwn
You set the correct permissions!
Round 3 (of 8)!

Current permissions of "/challenge/pwn": rwxr--rwx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r-xr--r-x
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod uo-w /challenge/pwn
You set the correct permissions!
Round 4 (of 8)!

Current permissions of "/challenge/pwn": r-xr--r-x
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r--r--r-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u-x /challenge/pwn
You set the correct permissions!
Round 5 (of 8)!

Current permissions of "/challenge/pwn": r--r--r-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ---r-----
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod uo-rx /challenge/pwn
You set the correct permissions!
Round 6 (of 8)!

Current permissions of "/challenge/pwn": ---r-----
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r--r-----
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+r /challenge/pwn
You set the correct permissions!
Round 7 (of 8)!

Current permissions of "/challenge/pwn": r--r-----
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r--------
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g-r /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{ED8y_MsPzFeAamjYAa0ppTYoeaF.dBTM2QDL5MTM1czW}
```
