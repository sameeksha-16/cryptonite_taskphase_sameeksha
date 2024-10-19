# CHAINING WITH SEMICOLONS
Here in this challenge instead of running the commands one after the other we learnt that we can run both the command /challege/pwn and /challenge/college together by separating them by a semi colon. 
```
Connected!
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn;/challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{wkEYTSZrL2Ef8GDHOsa1dUrVJ6Q.dVTN4QDL5MTM1czW}
```

# YOUR FIRST SHELL SCRIPT
Here in this challenge i created my first script called x.sh and inside that wrote```cat /flag```. Next by using the bash command i made it read the contents in my x.sh file and this gave me my flag.

```
Connected!
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{wB9qfnA7F6os9OH92Ux_rdxs_4V.dFzN4QDL5MTM1czW}
```

# REDIRECTING SCRIPT OUTPUT 
Here in this challenge we made use of the pipe operator to direct the output of ``` bash x.sh ``` into ```/challenge/solve```.
```
Connected!
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{I4Dy-RKsbZN6w7h4Y0hno02CWnl.dhTM5QDL5MTM1czW}
```

# EXECUTABLE SHELL SCRIPTS
Here I created a file using touch command and then entered the contents using echo command. Next i made the file execuetable using the chmod command.
```
Connected!
hacker@chaining~executable-shell-scripts:~$ touch s.sh
hacker@chaining~executable-shell-scripts:~$ echo /challenge/solve > ./s.sh
hacker@chaining~executable-shell-scripts:~$ chmod ugo+x s.sh
hacker@chaining~executable-shell-scripts:~$ ./s.sh
Congratulations on your shell script execution! Your flag:
pwn.college{QcsWsiiDXKFRzCircrZR_n_qBSq.dRzNyUDL5MTM1czW}
```
