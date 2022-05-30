---
layout: post
title: Vulnhub Jangow 01 Pentest
date: 2022-05-30 16:00:00
categories: [Pentest, Exploit]
---

# Jangow 01 Vulnhub Pentest

https://www.vulnhub.com/entry/jangow-101,754/

## Setup

Kali box and jangow 01 box on host only adapter (virtualbox)

## Enumeration

### Find target machine

ifconfig to find local ip range (192.168.56.1/24)

netdiscover -r 192.168.56.1/24

We see two machines at 192.168.56.100 & 192.168.56.102

### Determine which is the webserver

nmap -sV --top-ports 20 192.168.56.100-102

192.168.56.102 shows open ports 80 and 21 (ftp and http)

Machine doesn't allow for anonymous ftp login

### DirBuster Web Crawl

Used DirBuster dictionary attack to crawl through hosted webserver

Discovered potentially vulnerable /site/busque.php with parameter buscar

Passing bash commands in paramater buscar in the form of `busque.php?buscar=cmd` runs the command serverside and lists the output on the web page. This essentially provides us a bind shell which we can use to conduct a directory traversal attack on the webserver.

### Credential Harvesting

Examining config.php in the wordpress folder yields a username and password for a mysql db

Username: desafio02

Password: abygurl69

The mysql port is not open so we can not connect to it using these credentials. However the obtained credientials may be useful for other login purposes, if the user is guilty of password reuse.

Using these credentials to physically login to the machine was unsuccessful.

It's time to perform a directory traversal attack to obtain a username from /etc/passwd

Using cat /etc/passwd, I was able to locate a user named "jangow01" that was associated with our previous username "desafio02"

Using this newly obtained username and previous password as the credentials for a physical login was successful.

### Root access

Using uname -a, we find the linux kernal version

Exploit-db.com details CVE-2017-16995 which we will use for privilege execution

After downloading and compiling the exploit on the kali machine, I used ftp and the previous credentials to login and place the exploit in jangow01 home directory.

Executing the exploit successfully provided root privileges and this machine is successfully cracked.