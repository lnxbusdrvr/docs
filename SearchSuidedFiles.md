# Search for SUID/SGID files from system

It's security risk to have extra SUID/SGIDed files in system,
cause those files are run with root privileges and that is dangerous.

### Search for SUID files

```
find / -type f -perm -u+s -ls
```

/           Searches from / directory
-type f     Searches for type of file
-perm -u+s  Searches file permission of chmod u+s
-ls         lists found files


### Search for SGID files

```
find / -type f -perm -g+s -ls
```

-perm -g+s  Searches file permission of chmod g+s


### Search both SUID and SGID files

```
find / -type f -perm -u+s,g+s -ls
```






