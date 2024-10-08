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
