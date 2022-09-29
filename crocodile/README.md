# Crocodile

## Task 1

> What nmap scanning switch employs the use of default scripts during a scan?

`-sC`

Incidentally, if you enter this as `-Sc` you will also pass (wrongly).

## Task 2

> What service version is found to be running on port 21?

vsFTPd 3.0.3

```
─$ nmap -sC 10.129.236.106
Starting Nmap 7.92 ( https://nmap.org ) at 2022-09-21 20:57 EDT
Nmap scan report for 10.129.236.106
Host is up (0.038s latency).
Not shown: 998 closed tcp ports (conn-refused)
PORT   STATE SERVICE
21/tcp open  ftp
| ftp-syst:
|   STAT:
| FTP server status:
|      Connected to ::ffff:10.10.14.8
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 4
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| -rw-r--r--    1 ftp      ftp            33 Jun 08  2021 allowed.userlist
|_-rw-r--r--    1 ftp      ftp            62 Apr 20  2021 allowed.userlist.passwd
80/tcp open  http
|_http-title: Smash - Bootstrap Business Template

Nmap done: 1 IP address (1 host up) scanned in 2.91 seconds
```

## Task 3

> What FTP code is returned to us for the "Anonymous FTP login allowed" message?

230

## Task 4

> What command can we use to download the files we find on the FTP server?

get

```
ftp> get allowed.userlist -
remote: allowed.userlist
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for allowed.userlist (33 bytes).
aron
pwnmeow
egotisticalsw
admin
226 Transfer complete.
33 bytes received in 0.00 secs (89.5182 kB/s)
ftp> get allowed.userlist.passwd -
remote: allowed.userlist.passwd
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for allowed.userlist.passwd (62 bytes).
root
Supersecretpassword1
@BaASD&9032123sADS
rKXM59ESxesUFHAd
226 Transfer complete.
62 bytes received in 0.00 secs (93.8711 kB/s)
```

## Task 5

> What is one of the higher-privilege sounding usernames in the list we retrieved?

admin

## Task 6

> What version of Apache HTTP Server is running on the target host?

2.4.41

```
$ nmap -p80 -sV  10.129.236.106
Starting Nmap 7.92 ( https://nmap.org ) at 2022-09-21 21:17 EDT
Nmap scan report for 10.129.236.106
Host is up (0.032s latency).

PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 6.84 seconds
```

## Task 7

> What is the name of a handy web site analysis plug-in we can install in our browser?

Wappalyzer

* Wappalyzer - Technology profiler - Chrome Web Store  
  https://chrome.google.com/webstore/detail/wappalyzer-technology-pro/gppongmhjkpfnbhagpmjfkannfbllamg

## Task 8

> What switch can we use with gobuster to specify we are looking for specific filetypes?

-x (from preignition)

## Task 9

> What file have we found that can provide us a foothold on the target?

## Task 10

> Submit root flag

