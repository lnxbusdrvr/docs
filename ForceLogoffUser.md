# Logoff users by force & awoid users to login

### W to see who are logged right now

**w**  displays information about the users currently on the machine, and their processes.

```
w
```
Result:
```
 23:07:14 up 8 min,  2 users,  load average: 3,14, 2,57, 1,39
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
joe      tty7     :0               22:58    8:38  27.40s  0.14s twm
ken      pts/2    10.0.12.32       23:07    2.00s  0.09s  0.00s rm /etc/passwd
```


**1.Killing way**


Now let's see what's goin on on pts/2:
```
ps -dN | grep pts/2
``` 

Result:
```
3589 pts/2    00:00:00 bash
```

Now kill that process:
```
kill -9 3589
```

**2. Avoid users to login**

Just do this with user root:
```
touch /etc/nologin
```

Now users can't login

**More informative way**

Let's put some text to the file(run by root):
```
echo "No logins allowed. System is in maintance mode." > /etc/nologin
```

![login_failed](https://github.com/lnxbusdrvr/docs/blob/master/img/ForceLogoffUser.png)
