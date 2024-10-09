
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



# APPENDING OUTPUT 

Using '>' it re writes into the file. we use '>>' to use append into a given file. Here we appended the output of
/challenge/run into /home/hacker/the-flag ,next it checked if we passed all the tests or not and displayed the flag.
```
sameeksha03@DESKTOP-965QKSJ:~$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{AqAJK7Iaf3wbypbkK2YS0hAahtR.ddDM5QDL5MTM1czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```



# REDIRECTING ERRORS

Just like standard output, we can also redirect the error channel of commands.A File Descriptor (FD) is a number the describes a communication channel in Linux.FD 0: Standard Input,FD 1: Standard Output,FD 2: Standard Error. Here we directed the output of /challenge/run to myflag and the errors into instructions file.

```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{AUz6RIj8LfNhJ6GsPI1v46vbBUQ.ddjN1QDL5MTM1czW}
hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
```




# REDIRECTING INPUT

first w estored the value college into the pwn file and then we redirected this file into /challenge/run.
```Connected!
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{AoHAoUOvce0wjTOe-cuEDnqO6AB.dBzN1QDL5MTM1czW}
```


# GREPPING STORED RESULTS

here we Redirected the output of /challenge/run to /tmp/data.txt using '>'.it resulted in thousand lines of text, so we used grep command to get the flag from it.

```sameeksha03@DESKTOP-965QKSJ:~$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep 'pwn.college*' /tmp/data.txt
pwn.college{k3PzMC0gmInpcmUif0TBjkRIaec.dhTM4QDL5MTM1czW}
```


# GREPPING LIVE OUTPUT

In this case we don't require and middle file to find the required info from a file. The the pipe operator will connect the output of the content in left to the contnet(input) in right.
```Connected!
hacker@piping~grepping-live-output:~$ /challenge/run | grep 'pwn.college*'
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{Q_caDCWkJqh_C2qC7dOo0vwHA2R.dlTM4QDL5MTM1czW}
```

# grepping errors

The > operator redirects a given file descriptor to a file, and you've used 2> to redirect fd 2, which is standard error. The | operator redirects only standard output to another program, and there is no 2| form of the operator! It can only redirect standard output (file descriptor 1).
The shell has a >& operator, which redirects a file descriptor to another file descriptor. This means that we can have a two-step process to grep through errors: first, it redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|).

```
sameeksha03@DESKTOP-965QKSJ:~$  ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep "pwn.college*"
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{UZaivi5JQ3BbAGpAxiSjb2ovn4i.dVDM5QDL5MTM1czW}
```



# DUPLICATING PIPED DATA WITH TEE

we are using tee command to debugg code ,this command gives the  output of first command to the second command. the pipe symbol is used to connect the output and input of commands.

```
hacker@piping~duplicating-piped-data-with-tee:/$ /challenge/pwn | tee output | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:/$ cat output
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "QnpqlNt7"
hacker@piping~duplicating-piped-data-with-tee:/$ /challenge/pwn --secret "QnpqlNt7" | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{QnpqlNt7GVvXZpBzJ8nh98cs0X6.dFjM5QDL5MTM1czW}
```




# WRITING TO MULTIPLE PROGRAMS

here we learnt how tee command can be used to duplicate data to a file and a command.here it directed the output of /challenge/hack to /challenge/the and /challenge/planet.

```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
291661988475722870
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{scpmU_G2Y3AU0IAMA_kiWxMzsx-.dBDO0UDL5MTM1czW}
```



# SPLIT PIPING stderr and stdout

the | operator links the stdout of the left command with the stdin of the right command. and 2> redirects errors of /challenge/hack to /challenge/the.
```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{olkXX6en7tSATvDcw7-5sT7JPEs.dFDNwYDL5MTM1czW}
```
