# Network Troubleshooting #

**ping**
Syntax:
```
ping <ip-address, or host>
```
eg
```
ping www.google.com
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=122 time=17.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=122 time=18.0 ms
```
ttl = Time to Live. Shows how many packets. Can sometime find out what system is running by the ip/host
      default ttl list of the systems: (https://subinsb.com/default-device-ttl-values/)

**ping6**

**nc** (or **netcat**) utility is used for just about anything
under the sun involving TCP, UDP, or UNIX-domain sockets.

To test network: Open listening (-l) port:
```
nc -l <portnumber>
```
eg: ```nc -l 2388```

Now test it in other host:
Syntax:
```
nc <ip> <port>
Enter text here<enter>
```
eg:
```
nc 10.0.0.1 2388
Hello world
```
And now the "nc -l 2388" -window recieves the "Hello world" -text


**traceroute** tracks the route packets taken from an IP network on their way to a given host. It utilizes the IP protocol's time to live (TTL) field and attempts to elicit an ICMP TIME_EXCEEDED response from each gateway along the path to the host. 

Syntax: ```traceroute <address>```
eg: ```traceroute www.google.com```

**traceroute6** is for ipv6 addressess

**tracepath** and **tracepath6** do same thing as traceroute

