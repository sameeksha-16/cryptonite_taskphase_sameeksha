
# REDIRECTING OUTPUT
It is very similar to assigning or inputing value into a variable . We use '>' symbol to direct the value written on the left to the file mentioned on the right
```
Connected!
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{YqUvt_aV9S5kYrdc79YaDEMOL1C.dRjN1QDL5MTM1czW}
```


# REDIRECTING MORE OUTPUT

earlier we redirected the output of echo command into a file but in this challenge we directed the output of /challenge/run into myflag file. and to get the flag we simply read the contents using cat command
```Connected!
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ /flag
ssh-entrypoint: /flag: Permission denied
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{Y7mkZuVftynshjQ9suGZ2UBGNr-.dVjN1QDL5MTM1czW}
```
