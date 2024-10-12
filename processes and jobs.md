# LISTING PROCESSES
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


```Connected!
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{Yk_f1uHtVAJPNouCj1IuEOSvysI.dNDN4QDL5MTM1czW}```
