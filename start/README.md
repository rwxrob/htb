# Getting Started

Here's the stuff you need before you can even really get started on
HackTheBox.

## Problem with Ubuntu 22 being too new

The HackTheBox VPN is currently very insecure by only accepting MD5 and
SHA1 even though Ubuntu 22 and above require more. The *only* way around
this is to degrade the security of the VPN file to allow the insecure
algorithms to be used (which you can't change, only HTB can eventually
change that) by adding the following (thanks to @taniwha for finding
this out):

```
tls-cipher "DEFAULT:@SECLEVEL=0"
```

* linux mint - OpenSSL: error:0A00018E:SSL routines::ca md too weak - Super User  
  <https://superuser.com/questions/1737052/openssl-error0a00018essl-routinesca-md-too-weak>

## Beginner VPN is different from main VPN

In my case there are two VPN files required:

```
lab_rwxrob.ovpn
starting_point_rwxrob.ovpn
```

I keep these in the [vpn](vpn) directory but without actually committing
them to GitHub.

## Same "starting_point_\*.ovpn" file for free and vip

Just a note that after comparing the `ovpn` files they are identical for
the different pricing levels of HTB accounts.

