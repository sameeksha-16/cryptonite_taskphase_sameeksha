# THE PATH VARIABLE

```
Connected!
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{U2MPipjY3dhbhXDzE5dniLoyU_R.dZzNwUDL5MTM1czW}
```
# SETTING PATH

```
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{cGuznNeptYyJRW87lmP3qHF9AWU.dVzNyUDL5MTM1czW}
```

# ADDING COMMANDS
```
hacker@path~adding-commands:~$ mkdir -p /home/hacker/scripts
cd /home/hacker/scripts
hacker@path~adding-commands:~/scripts$ echo -e "#!/bin/bash\ncat /flag" > win
ssh-entrypoint: !/bin/bash\ncat: event not found
hacker@path~adding-commands:~/scripts$ nano /home/hacker/scripts/win
hacker@path~adding-commands:~/scripts$ chmod +x /home/hacker/scripts/win
hacker@path~adding-commands:~/scripts$ export PATH=/home/hacker/scripts:$PATH
hacker@path~adding-commands:~/scripts$ /challenge/run
Invoking 'win'....
pwn.college{UoVeTOCxJzCCdQEdihYZ62xZfAQ.dZzNyUDL5MTM1czW}
```
