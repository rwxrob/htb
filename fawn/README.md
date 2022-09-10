# Fawn

Okay, fine.

## Task 1

> What does the 3-letter acronym FTP stand for?

file transfer protocol (duh)

## Task 2

> Which port does the FTP service listen on usually?

21

```
grep ftp /etc/services
```

```out
ftp-data	20/tcp
ftp		21/tcp
tftp		69/udp
ftps-data	989/tcp				# FTP over SSL (data)
ftps		990/tcp
venus-se	2431/udp			# udp sftp side effect
codasrv-se	2433/udp			# udp sftp side effect
gsiftp		2811/tcp
zope-ftp	8021/tcp			# zope management by ftp
```

## Task 3

> What acronym is used for the secure version of FTP?

sftp

Because I've used it with secure shell. It uses the secure shell
protocol to tunnel.

## Task 4

> What is the command we can use to send an ICMP echo request to test our connection to the target?

ping

But really, any server admin worth their paycheck would disable ICMP
discovery completely so this is total bullshit. Here's some hardening
that people do to stop ICMP scans:

* https://gist.github.com/NikolaRHristov/937a37de58ac011747d607e56f90b989
* https://docs.vmware.com/en/VMware-NSX-T-Data-Center/3.2/administration/GUID-5ADD0FBB-7F30-4933-8737-2AC0D919EE3F.html

## Task 5

> From your scans, what version is FTP running on the target?

```
nmap -sV 10.129.11.185 
```

```out
Starting Nmap 7.80 ( https://nmap.org ) at 2022-09-09 22:40 EDT
Nmap scan report for 10.129.11.185
Host is up (0.030s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
Service Info: OS: Unix

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1.02 seconds
```

## Task 6

> From your scans, what OS type is running on the target? 

unix

## Task 7

> What is the command we need to run in order to display the 'ftp' client help menu?

ftp -h

Don't insult out intelligence.

## Task 8

> What is username that is used over FTP when you want to log in without having an account?

anonymous

## Task 9

> What is the response code we get for the FTP message 'Login successful'?

```
ftp 10.129.11.185

```

```out
╔ rwxrob@anton:htb(main)
╚ $ ftp 10.129.11.185
Connected to 10.129.11.185.
220 (vsFTPd 3.0.3)
Name (10.129.11.185:rwxrob): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>
```

## Task 10

> There are a couple of commands we can use to list the files and directories available on the FTP server. One is dir. What is the other that is a common way to list files on a Linux system.

ls

Of course.

## Task 11

> What is the command used to download the file we found on the FTP server?

get

But why the FUCK are you using FTP. Look up the wu-ftp hack, one of the
most famous.

## Task 12

> Submit root flag

037db22c881520061c53e0536e44f815

```
ftp> less flag.txt
```
