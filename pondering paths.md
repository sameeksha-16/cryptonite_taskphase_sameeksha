# THE ROOT
the path always begins with a '/' and is called absolute path

```sameeksha03@DESKTOP-965QKSJ:~$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{gB4eFc5gPZEdMtjNCspJKA40DqZ.dhzN5QDL5MTM1czW}

```

# PROGRAM AND ABSOLUTE PATHS

after connection
each directory can have other directories or files.here the challenge directory is in the root directory so /challenge. morover the run challenge is in the challenge directory so /challenge/run

```sameeksha03@DESKTOP-965QKSJ:~$  ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{I_jy6ejVGQbnyRNw-Eq8CE8Uh1c.dVDN1QDL5MTM1czW}
hacker@paths~program-and-absolute-paths:~$
```


# POSITION YET ELSEWHERE

```sameeksha03@DESKTOP-965QKSJ:~$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@paths~position-yet-elsewhere:~$ cd/
ssh-entrypoint: cd/: No such file or directory
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /var/lib/apt/lists
hacker@paths~position-yet-elsewhere:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{MAQs3nTohCI5NBI-IFK4LfpHGUa.dhDN1QDL5MTM1czW}

```

# IMPLICIT

for this first we need to enter into the root directory using cd then our cwd that is current working directory will become the root one.next we will run the challenge/run but this time without the / in front because our cwd is / already

```sameeksha03@DESKTOP-965QKSJ:~$  ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{UnD_8s9sKgbj2NVMWIm3rut_ccb.dlDN1QDL5MTM1czW}

```



# EXPLICIT
firstly we will go into the root directory, using cd/ then we will use ./challenge/run to run it . Here '.' helps us to remain in the same directory

```sameeksha03@DESKTOP-965QKSJ:~$  ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{sSc-DcIIYKXz5MUT6Y-NWEqqX4l.dBTN1QDL5MTM1czW}
```


# IMPLICIT RELATIVE PATH

```sameeksha03@DESKTOP-965QKSJ:~$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{A0SMSbc9TflGpoBamEbzIQgA7W7.dFTN1QDL5MTM1czW}

```


# HOME SWEET HOME

```sameeksha03@DESKTOP-965QKSJ:~$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@paths~home-sweet-home:~$ touch ~/m
hacker@paths~home-sweet-home:~$ /challenge/run ~/m
Writing the file to /home/hacker/m!
... and reading it back to you:
pwn.college{40jtMVWsV5Rdjq6eUd2zgd_w4VT.dNzM4QDL5MTM1czW}
```


# ELSEWERE
Here we were required to use the /challenge/run code on which it gave the path to the appropriate directory to which we were supposed to go. next i entered into the directory using cd command and again execueted the /challenge/run command which ultimately gave me the flag


```
sameeksha03@DESKTOP-965QKSJ:~$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@paths~position-elsewhere:~$ cd
hacker@paths~position-elsewhere:~$ /
ssh-entrypoint: /: Is a directory
hacker@paths~position-elsewhere:~$ cd/
ssh-entrypoint: cd/: No such file or directory
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /proc/67 directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /proc/67
hacker@paths~position-elsewhere:/proc/67$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{8CT151OMtf01i0JVdZaPMlCEuN0.ddDN1QDL5MTM1czW}

