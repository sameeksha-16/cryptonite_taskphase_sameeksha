#learning from documentation

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



#learning complex usage
here the --printfile has an argument(the path) /flag while it itself is an argument to /challenge/challenge

sameeksha03@DESKTOP-965QKSJ:~$  ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag




#reading manuals
here we use the man command followed by the argument and it gives the manual for the given argument. Using the information we can access to the flag

hacker@man~reading-manuals:~$ cd /
hacker@man~reading-manuals:/$ ./challenge
ssh-entrypoint: ./challenge: Is a directory
hacker@man~reading-manuals:/$ cd challenge
hacker@man~reading-manuals:/challenge$ ./challenge --ujdass 445
Correct usage! Your flag: pwn.college{QJujdFassPHBbLE4hRPIpKXibvl.dRTM4QDL5MTM1czW}
Correct argument! Here is the /flag file:
pwn.college{UDxpg-oZ9V2uXyqdYa3BpfHoXr9.dVjM5QDL5MTM1czW}



#searching manuals
to search use '/' followed by the keyword, it will highlight the mathches next use 'n' to go to next result and 'N' to go to the previous result.

sameeksha03@DESKTOP-965QKSJ:~$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ cd /
hacker@man~searching-manuals:/$ cd /challenge
hacker@man~searching-manuals:/challenge$ ./challenge  --snhl
Initializing...
Correct usage! Your flag: pwn.college{8iNZwcyDm8ySUottMFzFWxfjTq6.dVTM4QDL5MTM1czW}








# man man






# helpful programs
in this instead of man command we are using the --help command which gives us description how to get the flag. as in this case we had to use -p to get a secret number and then we used the -g (secret number ) to get the flag.

hacker@man~helpful-programs:/challenge$ ./challenge --print-value
The secret value is: 653
hacker@man~helpful-programs:/challenge$ ./challenge -g 653
Correct usage! Your flag: pwn.college{UsoKu6GBZur53Y9MJ--zyH0kbvZ.ddjM4QDL5MTM1czW}




# help for built ins
here the challenge is built-in we don't need to go into directories as we did before. using help challenge we got the neccesary info regarding options and the secret code ,using which we could get the flag.

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



