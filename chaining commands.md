#

# YOUR FIRST SHELL SCRIPT

```
Connected!
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{wB9qfnA7F6os9OH92Ux_rdxs_4V.dFzN4QDL5MTM1czW}
```

# REDIRECTING SCRIPT OUTPUT 

```
Connected!
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{I4Dy-RKsbZN6w7h4Y0hno02CWnl.dhTM5QDL5MTM1czW}
```

# EXECUTABLE SHELL SCRIPTS

```
Connected!
hacker@chaining~executable-shell-scripts:~$ touch s.sh
hacker@chaining~executable-shell-scripts:~$ echo /challenge/solve > ./s.sh
hacker@chaining~executable-shell-scripts:~$ chmod ugo+x s.sh
hacker@chaining~executable-shell-scripts:~$ ./s.sh
Congratulations on your shell script execution! Your flag:
pwn.college{QcsWsiiDXKFRzCircrZR_n_qBSq.dRzNyUDL5MTM1czW}
```
