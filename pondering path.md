# THE PATH VARIABLE
In this challenge, we need to make it so that /challenge/run cannot use the rm command in order to get flag.
Here we set the PATH to an empty string so that it couldn't accesss the rm command.
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
Here in this challenge on running the /challenge/run it searches for hw win command ,and this is present in the
directory '/challenge/more_commands/' so to access it we set the PATH to it and ran the /challenge/run command to get the flag.
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

# HIJACKING COMMANDS

```
Connected!
hacker@path~hijacking-commands:~$ mkdir ~/mybin
hacker@path~hijacking-commands:~$ echo "This is a fake rm command"
This is a fake rm command
hacker@path~hijacking-commands:~$ chmod +x ~/mybin/rm
chmod: cannot access '/home/hacker/mybin/rm': No such file or directory
hacker@path~hijacking-commands:~$ ls ~/mybin
hacker@path~hijacking-commands:~$ ls ~/mybin
hacker@path~hijacking-commands:~$ nano ~/mybin/rm
hacker@path~hijacking-commands:~$ chmod +x ~/mybin/rm
hacker@path~hijacking-commands:~$ rm
rm: missing operand
Try 'rm --help' for more information.
hacker@path~hijacking-commands:~$ echo $PATH
/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~hijacking-commands:~$ export PATH=~/mybin:$PATH
hacker@path~hijacking-commands:~$ ls -l ~/mybin/rm
-rwxr-xr-x 1 hacker hacker 72 Oct 18 10:04 /home/hacker/mybin/rm
hacker@path~hijacking-commands:~$ rm
This is a fake rm command. No files will be deleted.
hacker@path~hijacking-commands:~$ nano ~/mybin/rm
hacker@path~hijacking-commands:~$ rm
cat: /flag: Permission denied
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/mybin/rm. Executing!
pwn.college{kmWtc-E-vwqKPVUDFTGLtbk1CFF.ddzNyUDL5MTM1czW}
```
