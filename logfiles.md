# Captain's log stardate 42317.5

### Last

**last** searches back through the /var/log/wtmp file (or the file designated by the -f option) 
and displays a list of all users logged in (and out) since that file was created.

Useful command:
```
last -d
```
Shows logins out from local host i.e. from internet.

### Lastlog

**lastlog** formats and prints the contents of the last login log /var/log/lastlog file.
The login-name, port, and last login time will be printed.

### Who

**who** print information about users who are currently logged in.

### Finger

**finger** displays information about the system users.

### Fuser

**fuser** displays the PIDs of processes using the specified files or file systems.

Examples:

Shows who runs gimp:<br>
```
fuser -u /usr/bin/gimp
``` <br>
result: <br>
```
/usr/bin/gimp-2.8:   20172e(joe)
``` <br>
Joe is running gimp with PID of 20172

-u  shows username
e   Means that it is excecutable beign run.

***What those letters mean?***

c      current directory.
e      executable being run.
f      open file.  f is omitted in default display mode.
F      open file for writing.  F is omitted in default display mode.
r      root directory.
m      mmap'ed file or shared library.
.      Placeholder, omitted in default display mode.










