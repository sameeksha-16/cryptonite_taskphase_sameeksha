# LISTING PROCESSES
Here in this challenge the /challenge/run file has been renamed into a random filename and  i used the ps -ef command to get it .
```
Connected!
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 14:42 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /ru
root           7       1  0 14:42 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 14:42 ?        00:00:00 /challenge/11505-run-13446
root          72      68  0 14:42 ?        00:00:00 sleep 6h
hacker        73       0  0 14:42 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        90       0  0 14:44 pts/1    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker       107      90  0 14:44 pts/1    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/11505-run-13446
Yahaha, you found me! Here is your flag:
pwn.college{gawt3OSGg4qqdjE0IjeUA6Xdp2M.dhzM4QDL5MTM1czW}
Now I will sleep for a while (so that you could find me with 'ps').
```
# KILLING PROCESSES

Here in this challenge we learnt how to stop certain processes from running by using the kill command. the command goes like ``` kill <pid>```. The pid number can be extracted using the ps -e command . In this case i tried to stop the process by using ```kill 94``` but i still couldn't run the ```/challenge/run``` as it displayed the dont_run process was still running. So i used ps aux to checke if it still exists , i got the pid as 73 and stopped it using ```kill 73```. Lastly i ran the /challenge/run command to get the flag.

```Connected!
hacker@processes~killing-processes:~$ ps -e
    PID TTY          TIME CMD
      1 ?        00:00:00 docker-init
      7 ?        00:00:00 /run/dojo/bin/s
     71 ?        00:00:00 su
     73 ?        00:00:00 bash
     74 ?        00:00:00 sleep
     75 pts/0    00:00:00 ssh-entrypoint
     94 pts/0    00:00:00 dont_run
     95 pts/0    00:00:00 sleep
     96 pts/1    00:00:00 ssh-entrypoint
    113 pts/1    00:00:00 ps
hacker@processes~killing-processes:~$ kill 94
hacker@processes~killing-processes:~$ ps -e | grep dont_run
hacker@processes~killing-processes:~$ /challenge/run
Nope! /challenge/dont_run is still running! You gotta terminate it before I
give you the flag!
hacker@processes~killing-processes:~$ ps -e
    PID TTY          TIME CMD
      1 ?        00:00:00 docker-init
      7 ?        00:00:00 /run/dojo/bin/s
     71 ?        00:00:00 su
     73 ?        00:00:00 bash
     74 ?        00:00:00 sleep
     75 pts/0    00:00:00 ssh-entrypoint
     95 pts/0    00:00:00 sleep
     96 pts/1    00:00:00 ssh-entrypoint
    120 pts/1    00:00:00 ps
hacker@processes~killing-processes:~$ /challenge/run
Nope! /challenge/dont_run is still running! You gotta terminate it before I
give you the flag!
hacker@processes~killing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   14:57   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bi
root           7  0.0  0.0   5052  2560 ?        S    14:57   0:00 /run/dojo/bin/sleep 6h
root          71  0.0  0.0   4732  2880 ?        S    14:57   0:00 su -c /challenge/.launcher hacker
hacker        73  0.0  0.0   4976  3200 ?        Ss   14:57   0:00 /challenge/dont_run
hacker        74  0.0  0.0   5052  2560 ?        S    14:57   0:00 sleep 6h
hacker        75  0.0  0.0   5372  4160 pts/0    Ss+  14:57   0:00 /run/dojo/bin/ssh-entrypoint
hacker        95  0.0  0.0   5052  2240 pts/0    S    14:58   0:00 sleep 6h
hacker        96  0.0  0.0   5372  4160 pts/1    Ss   15:19   0:00 /run/dojo/bin/ssh-entrypoint
hacker       135  0.0  0.0   7868  3520 pts/1    R+   15:25   0:00 ps aux
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{kG9QfOSwFU9K3J70obnB-A4b3Sk.dJDN4QDL5MTM1czW}
```
# INTERUPPTING PROCESSES
Here in this challenge, we can suspend the current running process using the ```Ctrl -C ``` command.

```Connected!
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{Yk_f1uHtVAJPNouCj1IuEOSvysI.dNDN4QDL5MTM1czW}
```

# SUSPENDING PROCESSES
To suspend the current running process , the ```Ctrl-Z``` command is used. Here we first ran the command ```/challenge/run``` command then we suspended the process and ran the same command again to ge the command.
```
Connected!
hacker@processes~suspending-processes:~$ ./run
ssh-entrypoint: ./run: No such file or directory
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          83      65  0 15:50 pts/0    00:00:00 bash /challenge/run
root          85      83  0 15:50 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          83      65  0 15:50 pts/0    00:00:00 bash /challenge/run
root          90      65  0 15:51 pts/0    00:00:00 bash /challenge/run
root          92      90  0 15:51 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{8XvUfMGyHG1KzUjypBn3z50Pe3q.dVDN4QDL5MTM1czW}
```


# RESUMING PROCESSES
The processes which we suspended will come in use in future as it has been resumed and not deleted, so we activate it using the ```fg``` command. Here at the end we ran the command ```/challenge/run``` to get the flag.

```
Connected!
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{g1KlCq1xi-TN9PwC0hMMnCpEJhU.dZDN4QDL5MTM1czW}
Don't forget to press Enter to quit me!
```

# BACKGROUNDING PROCESSES

Here in this challenge first we ran the command ```/challenge/run``` then we suspended it using the Ctrl-Z, and then we activated it in the background using the ```bg``` command. Next we relaunched it and got the required flag.

```Connected!
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S+   bash /challenge/run
root          84 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 T    bash /challenge/run
root          89 S+   bash /challenge/run
root          91 R+   ps -o user=UID,pid,stat,cmd

I found a second version of me, but it's suspended! Please resume it in the
background with the 'bg' command, then run me again.
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S    bash /challenge/run
root         103 S    sleep 6h
root         104 S+   bash /challenge/run
root         106 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{sZIPv2tzP3TPYsAOBhH5R5cK0SX.ddDN4QDL5MTM1czW}
```

# FOREGROUNDING PROCESSES
Here we ran the command ```/challenge/run```, then we suspended the current process by clicking Ctrl-Z, and let it run in the background usinh ```bg``` command. Next we made it run in the front using ```fg``` command,and finally pressed enter key to get the flag.
```
Connected!
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{IGUhHPk0W9vhOiieh0e5LgjNa0B.dhDN4QDL5MTM1czW}
```
# STARTING BACKGROUND PROCESSES

Here in this challenge we ran the /challenge/run command in the background aand then we followed the instructions to get the flag

```Connected!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run
You've started me in the foreground! You must start me in the background (by
appending '&' to the command) to get the flag!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 102
Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...
hacker@processes~starting-backgrounded-processes:~$
Anyways! Here is your flag!
pwn.college{M40qUwrEo_eSiLvS9jN0H9P_zjs.dlDN4QDL5MTM1czW}
```

# PROCESS EXIT CODES
Here in this challenge we ran the ```/challenge/get-code $?``` command followed by ```echo``` command to get the secret code. Next we wrote the code as an argument to ``` /challenge/submit-code``` and got the flag.

```
Connected!
hacker@processes~process-exit-codes:~$ /challenge/get-code $?
Exiting with an error code!
hacker@processes~process-exit-codes:~$echo /challenge/get-code $?
/challenge/get-code 8
hacker@processes~process-exit-codes:~$ /challenge/submit-code 8
CORRECT! Here is your flag:
pwn.college{0AKBWEWSdx8NJR15W32KAyInoFm.dljN4UDL5MTM1czW}
```
