# Meow

OMG, do I have to?

## Task 1

> What does the acronym VM stand for?

virtual machine

## Task 2

> What tool do we use to interact with the operating system in order to issue commands via the command line, such as the one to start our VPN connection? It's also known as a console or shell.

**terminal**

## Task 3

> What service do we use to form our VPN connection into HTB labs?

openvpn

Had to install and set this all up well before this moment. Look at
[`start`](start) for details.

## Task 4

> What is the abbreviated name for a 'tunnel interface' in the output of your VPN boot-up sequence output?

tun

Use `ip -c a` to see it.

## Task 5

> What tool do we use to test our connection to the target with an ICMP echo request?

ping

```
ping 10.129.205.137
```

```out
PING 10.129.205.137 (10.129.205.137) 56(84) bytes of data.
64 bytes from 10.129.205.137: icmp_seq=1 ttl=63 time=34.7 ms
64 bytes from 10.129.205.137: icmp_seq=3 ttl=63 time=33.7 ms
64 bytes from 10.129.205.137: icmp_seq=4 ttl=63 time=39.1 ms
64 bytes from 10.129.205.137: icmp_seq=5 ttl=63 time=45.4 ms

--- 10.129.205.137 ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4012ms
rtt min/avg/max/mdev = 33.716/38.223/45.394/4.618 ms
```

## Task 6

> What is the name of the most common tool for finding open ports on a target?

nmap

```
nmap 10.129.205.137
```

```out
Starting Nmap 7.80 ( https://nmap.org ) at 2022-09-09 21:43 EDT
Nmap scan report for 10.129.205.137
Host is up (0.033s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
23/tcp open  telnet

Nmap done: 1 IP address (1 host up) scanned in 0.60 seconds
```

## Task 7

> What service do we identify on port 23/tcp during our scans?

telnet

I just guessed because I knew it from long ago.

## Task 8

> What username is able to log into the target over telnet with a blank password?

root

## Task 9

Submit root flag.

```
root@Meow:~# cat flag.txt
b40abdfe23665f766f9c61ecba8a4c19
```

