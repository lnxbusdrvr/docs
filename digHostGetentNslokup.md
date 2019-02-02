# Dig, host, getent, nslookup #
**Nslookup**
is a program to query Internet domain name servers.
```
nslookup www.google.com
```
result:
```
Server:		10.119.0.1
Address:	10.119.0.1#53

Non-authoritative answer:
Name:	www.google.com
Address: 216.58.209.132
Name:	www.google.com
Address: 2a00:1450:400f:806::2004
```
**dig** is a flexible tool for interrogating DNS name servers.
```
dig www.google.com
```
result:
```

; <<>> DiG 9.11.3-1ubuntu1.3-Ubuntu <<>> www.google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 6052
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;www.google.com.			IN	A

;; ANSWER SECTION:
www.google.com.		667	IN	A	216.58.209.132

;; Query time: 14 msec
;; SERVER: 10.119.0.1#53(10.119.0.1)
;; WHEN: Sat Feb 02 19:02:37 EET 2019
;; MSG SIZE  rcvd: 59``

```
**host** is a simple utility for performing DNS lookups.
```
host www.google.com
```
result:
```
www.google.com has address 172.217.21.132
www.google.com has IPv6 address 2a00:1450:400f:809::2004

```

Looking host throught different dns-server (8.8.8.8)
```
host www.google.com 8.8.8.8
```
result:
```
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases: 

google.com has address 172.217.21.142
google.com has IPv6 address 2a00:1450:400f:80a::200e
google.com mail is handled by 40 alt3.aspmx.l.google.com.
google.com mail is handled by 20 alt1.aspmx.l.google.com.
google.com mail is handled by 10 aspmx.l.google.com.
google.com mail is handled by 50 alt4.aspmx.l.google.com.
google.com mail is handled by 30 alt2.aspmx.l.google.com.
```

**getent** command displays entries from databases supported by
the Name Service Switch libraries, which are configured in /etc/nss‐witch.conf.
Syntax:
```
getent hosts <localhost>
```
Example througt DNS lookup
```
getent hosts www.google.com
```
result:
```
2a00:1450:400f:804::2004 www.google.com`

```
