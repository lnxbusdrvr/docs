# Chage, Umlimit - User restrictions on Linux

**chage** command changes the number of days between password changes and the date of the last password change.

NB! It's chage, not change

Syntax:
```
change -M <how_many_days> -W <warn_days_before_expiring_password> <username>
```
eg:
```
change -M 30 -W 7 joe
```

-M 30 Set password to expire in 30 days<br>
-W Warning the user 7 days before password expires<br>
joe For user joe<br>



### pam_limits in /etc/security/limits.conf

**pam_limits PAM** module sets limits on the system resources that can be obtained in a user-session.
Users of uid=0 are affected by this limits, too.

Where:<br>
<domain> can be:<br>
        - a user name<br>
        - a group name, with @group syntax<br>
        - the wildcard *, for default entry<br>
        - the wildcard %, can be also used with %group syntax,<br>
                 for maxlogin limit<br>
        - NOTE: group and wildcard limits are not applied to root.<br>
          To apply a limit to the root user, <domain> must be<br>
          the literal username root.<br>

<type> can have the two values:<br>
        - "soft" for enforcing the soft limits<br>
soft means that it can be exceeded temporary
        - "hard" for enforcing hard limits<br>
hard means that it can never be exceeded

<item> can be one of the following:<br>
        - core - limits the core file size (KB)<br>
        - data - max data size (KB)<br>
        - fsize - maximum filesize (KB)<br>
        - memlock - max locked-in-memory address space (KB)<br>
        - nofile - max number of open files<br>
        - rss - max resident set size (KB)<br>
        - stack - max stack size (KB)<br>
        - cpu - max CPU time (MIN)<br>
        - nproc - max number of processes<br>
        - as - address space limit (KB)<br>
        - maxlogins - max number of logins for this user<br>
        - maxsyslogins - max number of logins on the system<br>
        - priority - the priority to run user process with<br>
        - locks - max number of file locks the user can hold<br>
        - sigpending - max number of pending signals<br>
        - msgqueue - max memory used by POSIX message queues (bytes)<br>
        - nice - max nice priority allowed to raise to values: [-20, 19]<br>
        - rtprio - max realtime priority<br>
        - chroot - change root to directory (Debian-specific)<br>

eg:
```
joe soft  cpu       10
ken hard  maxlogin  2
```

Means that:<br>
joe can temporarly exceeded cpu time use in 15 mins<br>
ken can login only 2 times at once

btw. You can see your cpu time with this command:<br>
```
ps -eo pcpu,pid,user,args | sort -k 1 -r | head -5
```

You can attach that command with **watch -n 1** to cycle it every 1 second:<br>
```
watch -n 1 'ps -eo pcpu,pid,user,args | sort -k 1 -r | head -5'
```

### ulimit

**ulimit**() call will get or set some limit for the calling process.<br>

Difference between /etc/security/limits.conf and ulimit is that ulimit limits affects only commands 
run in command prompt, but pam_limit limits affect whole system including GUI/X11/Wayland etc.

Syntax:
´´´
ulimit <options> limit
```

options:

-c  Maximum size of core file in blocks<br>
-f  Maximum size in blocks of files created<br>
-n  Maximum sixe of open files<br>
-t  Maximum cpu time in seconds<br>
-u  Maximum number of processes by user<br>
-d  Maximum size of processes's data segment in RAM<br>
-m  Maximum resident size of a processes in RAM
-s  Maximun of stack file  
-H  Is used to set hard limit
-S  Is used to set soft limit
-a  Show currently set limits

e.g.
```
ulimit -S -u 50
``` <br>
Sets soft limit for running processes to 50 processes

