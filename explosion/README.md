# Explosion

## Task 1

> What does the 3-letter acronym RDP stand for?

remote desktop protocol

## Task 2

> What is a 3-letter acronym that refers to interaction with the host through a command line interface?

cli

ARE YOU FUCKING KIDDING ME WITH THIS KINDERGARTEN SHIT!!

## Task 3

> What about graphical user interface interactions?

gui

Cuz I'm a fucking genius.

## Task 4

> What is the name of an old remote access tool that came without encryption by default and listens on TCP port 23?

telnet

## Task 5

> What is the name of the service running on port 3389 TCP?

```
grep 3389 /etc/services
```

```out
ms-wbt-server	3389/tcp
```

## Task 6

> What is the switch used to specify the target host's IP address when using xfreerdp?

```
/v:
```

I totally guessed from `man xfreerdp` in the usage section.

## Task 7

> What username successfully returns a desktop projection to us with a blank password?

administrator

Lucky guess but still need X11 full GUI support and forwarding to get
the flag next.

## Task 8

> Submit root flag

951fa96d7830c451b536be5a6be008a0

Need to fire up a VM that has X11 support for this. I downloaded the
Kali VM with `kali`/`kali` user and password.

```
DISPLAY=:0.0 xfreerdp /v:10.129.188.252 /u:administrator
```
