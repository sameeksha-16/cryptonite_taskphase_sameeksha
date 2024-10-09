# LEARNING FROM DOCUMENTATION
```
sameeksha03@DESKTOP-965QKSJ:~$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@man~learning-from-documentation:~$ cd /
hacker@man~learning-from-documentation:/$ /challenge/challenge ---giveflag
Incorrect usage! You passed the wrong argument (read the challenge description
for details).
hacker@man~learning-from-documentation:/$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{4Oh15mjGOmk0DgDZurPBYGskiYr.dRjM5QDL5MTM1czW}
hacker@man~learning-from-documentation:/$
```


# LEARNING COMPLEX USAGE
here the --printfile has an argument(the path) /flag while it itself is an argument to /challenge/challenge
```
sameeksha03@DESKTOP-965QKSJ:~$  ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag

```


# READING MANUALS
here we use the man command followed by the argument and it gives the manual for the given argument. Using the information we can access to the flag

```
hacker@man~reading-manuals:~$ cd /
hacker@man~reading-manuals:/$ ./challenge
ssh-entrypoint: ./challenge: Is a directory
hacker@man~reading-manuals:/$ cd challenge
hacker@man~reading-manuals:/challenge$ ./challenge --ujdass 445
Correct usage! Your flag: pwn.college{QJujdFassPHBbLE4hRPIpKXibvl.dRTM4QDL5MTM1czW}
Correct argument! Here is the /flag file:
pwn.college{UDxpg-oZ9V2uXyqdYa3BpfHoXr9.dVjM5QDL5MTM1czW}

```

# SEARCHING MANUALS
to search use '/' followed by the keyword, it will highlight the mathches next use 'n' to go to next result and 'N' to go to the previous result.

```
sameeksha03@DESKTOP-965QKSJ:~$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ cd /
hacker@man~searching-manuals:/$ cd /challenge
hacker@man~searching-manuals:/challenge$ ./challenge  --snhl
Initializing...
Correct usage! Your flag: pwn.college{8iNZwcyDm8ySUottMFzFWxfjTq6.dVTM4QDL5MTM1czW}



```




# MAN MAN 
First we read the manual for man command. then used the given information to get the unknown manpage into which flag was hidden that is wdoyaddaqi in this case. next we used the /challenge/challenge command to get the flag by inputing the number mentioned.

```
sameeksha03@DESKTOP-965QKSJ:~$ ssh -i ./key hacker@dojo.pwn.college
                                                                Connected!
hacker@man~searching-for-manuals:~$ man man
MAN(1)                Manual pager utils                MAN(1)

NAME
       man - an interface to the system reference manuals

SYNOPSIS
       man [man options] [[section] page ...] ...
       man -k [apropos options] regexp ...
       man -K [man options] [section] term ...
       man -f [whatis options] page ...
       man -l [man options] file ...
       man -w|-W [man options] page ...

DESCRIPTION
       man  is  the system's manual pager.  Each page argument
hacker@man~searching-for-manuals:~$  man -k /challenge/challenge
wdoyaddaqi (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man wdoyaddaqi

CHALLENGE(1)                                            Challenge Commands                                           CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --wdoyad NUM
              print the flag if NUM is 900

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                  May 2024                                                CHALLENGE(1)
hacker@man~searching-for-manuals:~$ /challenge/challenge --wdoyad 900
Correct usage! Your flag: pwn.college{wQ90dS0RoyEadAdaqi5KfcfKp1H.dZTM4QDL5MTM1czW}
```




# HELPFUL PROGRAMS

In this instead of man command we are using the --help command which gives us description how to get the flag. as in this case we had to use -p to get a secret number and then we used the -g (secret number ) to get the flag.

```
hacker@man~helpful-programs:/challenge$ ./challenge --print-value
The secret value is: 653
hacker@man~helpful-programs:/challenge$ ./challenge -g 653
Correct usage! Your flag: pwn.college{UsoKu6GBZur53Y9MJ--zyH0kbvZ.ddjM4QDL5MTM1czW}


```

# HELP WITH BUILTINS

here the challenge is built-in we don't need to go into directories as we did before. using help challenge we got the neccesary info regarding options and the secret code ,using which we could get the flag.
```
Connected!
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "MXFC3hB-".
hacker@man~help-for-builtins:~$ challenge --secret MXFC3hB-
Correct! Here is your flag!
pwn.college{MXFC3hB-wLWNCGrQPqv4O53i_F8.dRTM5QDL5MTM1czW}
```

```

