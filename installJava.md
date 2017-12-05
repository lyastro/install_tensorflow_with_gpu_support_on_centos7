$ sudo yum install java -y
[sudo] password for liangyu: 
Loaded plugins: fastestmirror, langpacks
base                                                                                                                                                                                                    | 3.6 kB  00:00:00     
cuda                                                                                                                                                                                                    | 2.5 kB  00:00:00     
epel/x86_64/metalink                                                                                                                                                                                    | 5.4 kB  00:00:00     
epel                                                                                                                                                                                                    | 4.3 kB  00:00:00     
extras                                                                                                                                                                                                  | 3.4 kB  00:00:00     
updates                                                                                                                                                                                                 | 3.4 kB  00:00:00     
(1/6): base/7/x86_64/primary_db                                                                                                                                                                         | 5.7 MB  00:00:01     
(2/6): base/7/x86_64/group_gz                                                                                                                                                                           | 156 kB  00:00:02     
(3/6): epel/x86_64/updateinfo                                                                                                                                                                           | 827 kB  00:00:02     
(4/6): extras/7/x86_64/primary_db                                                                                                                                                                       | 101 kB  00:00:00     
(5/6): epel/x86_64/primary_db                                                                                                                                                                           | 4.8 MB  00:00:04     
(6/6): updates/7/x86_64/primary_db                                                                                                                                                                      | 2.8 MB  00:00:04     
Determining fastest mirrors
 * base: mirrors.aliyun.com
 * epel: mirrors.tuna.tsinghua.edu.cn
 * extras: mirrors.tuna.tsinghua.edu.cn
 * updates: mirrors.sohu.com
Resolving Dependencies
--> Running transaction check
---> Package java-1.8.0-openjdk.x86_64 1:1.8.0.141-1.b16.el7_3 will be updated
---> Package java-1.8.0-openjdk.x86_64 1:1.8.0.144-0.b01.el7_4 will be an update
--> Processing Dependency: java-1.8.0-openjdk-headless(x86-64) = 1:1.8.0.144-0.b01.el7_4 for package: 1:java-1.8.0-openjdk-1.8.0.144-0.b01.el7_4.x86_64
--> Running transaction check
---> Package java-1.8.0-openjdk-headless.x86_64 1:1.8.0.141-1.b16.el7_3 will be updated
---> Package java-1.8.0-openjdk-headless.x86_64 1:1.8.0.144-0.b01.el7_4 will be an update
--> Processing Dependency: nss-softokn(x86-64) >= 3.28.3 for package: 1:java-1.8.0-openjdk-headless-1.8.0.144-0.b01.el7_4.x86_64
--> Processing Dependency: copy-jdk-configs >= 2.2 for package: 1:java-1.8.0-openjdk-headless-1.8.0.144-0.b01.el7_4.x86_64
--> Running transaction check
---> Package copy-jdk-configs.noarch 0:1.2-1.el7 will be updated
---> Package copy-jdk-configs.noarch 0:2.2-3.el7 will be an update
---> Package nss-softokn.x86_64 0:3.16.2.3-14.4.el7 will be updated
--> Processing Dependency: nss-softokn(x86-64) = 3.16.2.3-14.4.el7 for package: nss-softokn-devel-3.16.2.3-14.4.el7.x86_64
---> Package nss-softokn.x86_64 0:3.28.3-8.el7_4 will be an update
--> Processing Dependency: nss-softokn-freebl(x86-64) >= 3.28.3-8.el7_4 for package: nss-softokn-3.28.3-8.el7_4.x86_64
--> Running transaction check
---> Package nss-softokn-devel.x86_64 0:3.16.2.3-14.4.el7 will be updated
---> Package nss-softokn-devel.x86_64 0:3.28.3-8.el7_4 will be an update
--> Processing Dependency: nss-softokn-freebl-devel(x86-64) = 3.28.3-8.el7_4 for package: nss-softokn-devel-3.28.3-8.el7_4.x86_64
---> Package nss-softokn-freebl.x86_64 0:3.16.2.3-14.4.el7 will be updated
---> Package nss-softokn-freebl.x86_64 0:3.28.3-8.el7_4 will be an update
--> Running transaction check
---> Package nss-softokn-freebl-devel.x86_64 0:3.16.2.3-14.4.el7 will be updated
---> Package nss-softokn-freebl-devel.x86_64 0:3.28.3-8.el7_4 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

===============================================================================================================================================================================================================================
 Package                                                          Arch                                        Version                                                       Repository                                    Size
===============================================================================================================================================================================================================================
Updating:
 java-1.8.0-openjdk                                               x86_64                                      1:1.8.0.144-0.b01.el7_4                                       updates                                      238 k
Updating for dependencies:
 copy-jdk-configs                                                 noarch                                      2.2-3.el7                                                     base                                          18 k
 java-1.8.0-openjdk-headless                                      x86_64                                      1:1.8.0.144-0.b01.el7_4                                       updates                                       32 M
 nss-softokn                                                      x86_64                                      3.28.3-8.el7_4                                                updates                                      310 k
 nss-softokn-devel                                                x86_64                                      3.28.3-8.el7_4                                                updates                                       27 k
 nss-softokn-freebl                                               x86_64                                      3.28.3-8.el7_4                                                updates                                      214 k
 nss-softokn-freebl-devel                                         x86_64                                      3.28.3-8.el7_4                                                updates                                       49 k

Transaction Summary
===============================================================================================================================================================================================================================
Upgrade  1 Package (+6 Dependent packages)

Total download size: 32 M
Downloading packages:
No Presto metadata available for base
updates/7/x86_64/prestodelta                                                                                                                                                                            | 242 kB  00:00:00     
Delta RPMs reduced 810 k of updates to 364 k (55% saved)
(1/7): java-1.8.0-openjdk-1.8.0.141-1.b16.el7_3_1.8.0.144-0.b01.el7_4.x86_64.drpm                                                                                                                       |  62 kB  00:00:00     
(2/7): nss-softokn-3.16.2.3-14.4.el7_3.28.3-8.el7_4.x86_64.drpm                                                                                                                                         | 174 kB  00:00:00     
(3/7): nss-softokn-freebl-3.16.2.3-14.4.el7_3.28.3-8.el7_4.x86_64.drpm                                                                                                                                  |  95 kB  00:00:00     
(4/7): nss-softokn-freebl-devel-3.16.2.3-14.4.el7_3.28.3-8.el7_4.x86_64.drpm                                                                                                                            |  33 kB  00:00:00     
(5/7): nss-softokn-devel-3.28.3-8.el7_4.x86_64.rpm                                                                                                                                                      |  27 kB  00:00:00     
(6/7): copy-jdk-configs-2.2-3.el7.noarch.rpm                                                                                                                                                            |  18 kB  00:00:00     
(7/7): java-1.8.0-openjdk-headless-1.8.0.144-0.b01.el7_4.x86_64.rpm                                                                                                                                     |  32 MB  00:00:12     
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                                                          2.5 MB/s |  32 MB  00:00:13     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Updating   : nss-softokn-freebl-3.28.3-8.el7_4.x86_64                                                                                                                                                                   1/14 
  Updating   : nss-softokn-3.28.3-8.el7_4.x86_64                                                                                                                                                                          2/14 
  Updating   : nss-softokn-freebl-devel-3.28.3-8.el7_4.x86_64                                                                                                                                                             3/14 
  Updating   : copy-jdk-configs-2.2-3.el7.noarch                                                                                                                                                                          4/14 
  Updating   : 1:java-1.8.0-openjdk-headless-1.8.0.144-0.b01.el7_4.x86_64                                                                                                                                                 5/14 
warning: /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.144-0.b01.el7_4.x86_64/jre/lib/security/nss.cfg created as /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.144-0.b01.el7_4.x86_64/jre/lib/security/nss.cfg.rpmnew
restored /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.144-0.b01.el7_4.x86_64/jre/lib/security/nss.cfg.rpmnew to /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.144-0.b01.el7_4.x86_64/jre/lib/security/nss.cfg
  Updating   : 1:java-1.8.0-openjdk-1.8.0.144-0.b01.el7_4.x86_64                                                                                                                                                          6/14 
  Updating   : nss-softokn-devel-3.28.3-8.el7_4.x86_64                                                                                                                                                                    7/14 
  Cleanup    : nss-softokn-devel-3.16.2.3-14.4.el7.x86_64                                                                                                                                                                 8/14 
  Cleanup    : nss-softokn-freebl-devel-3.16.2.3-14.4.el7.x86_64                                                                                                                                                          9/14 
  Cleanup    : 1:java-1.8.0-openjdk-1.8.0.141-1.b16.el7_3.x86_64                                                                                                                                                         10/14 
  Cleanup    : 1:java-1.8.0-openjdk-headless-1.8.0.141-1.b16.el7_3.x86_64                                                                                                                                                11/14 
  Cleanup    : nss-softokn-3.16.2.3-14.4.el7.x86_64                                                                                                                                                                      12/14 
  Cleanup    : copy-jdk-configs-1.2-1.el7.noarch                                                                                                                                                                         13/14 
  Cleanup    : nss-softokn-freebl-3.16.2.3-14.4.el7.x86_64                                                                                                                                                               14/14 
  Verifying  : 1:java-1.8.0-openjdk-1.8.0.144-0.b01.el7_4.x86_64                                                                                                                                                          1/14 
  Verifying  : nss-softokn-freebl-devel-3.28.3-8.el7_4.x86_64                                                                                                                                                             2/14 
  Verifying  : nss-softokn-3.28.3-8.el7_4.x86_64                                                                                                                                                                          3/14 
  Verifying  : nss-softokn-devel-3.28.3-8.el7_4.x86_64                                                                                                                                                                    4/14 
  Verifying  : 1:java-1.8.0-openjdk-headless-1.8.0.144-0.b01.el7_4.x86_64                                                                                                                                                 5/14 
  Verifying  : copy-jdk-configs-2.2-3.el7.noarch                                                                                                                                                                          6/14 
  Verifying  : nss-softokn-freebl-3.28.3-8.el7_4.x86_64                                                                                                                                                                   7/14 
  Verifying  : nss-softokn-freebl-devel-3.16.2.3-14.4.el7.x86_64                                                                                                                                                          8/14 
  Verifying  : nss-softokn-freebl-3.16.2.3-14.4.el7.x86_64                                                                                                                                                                9/14 
  Verifying  : nss-softokn-devel-3.16.2.3-14.4.el7.x86_64                                                                                                                                                                10/14 
  Verifying  : 1:java-1.8.0-openjdk-1.8.0.141-1.b16.el7_3.x86_64                                                                                                                                                         11/14 
  Verifying  : nss-softokn-3.16.2.3-14.4.el7.x86_64                                                                                                                                                                      12/14 
  Verifying  : 1:java-1.8.0-openjdk-headless-1.8.0.141-1.b16.el7_3.x86_64                                                                                                                                                13/14 
  Verifying  : copy-jdk-configs-1.2-1.el7.noarch                                                                                                                                                                         14/14 

Updated:
  java-1.8.0-openjdk.x86_64 1:1.8.0.144-0.b01.el7_4                                                                                                                                                                            

Dependency Updated:
  copy-jdk-configs.noarch 0:2.2-3.el7                  java-1.8.0-openjdk-headless.x86_64 1:1.8.0.144-0.b01.el7_4           nss-softokn.x86_64 0:3.28.3-8.el7_4           nss-softokn-devel.x86_64 0:3.28.3-8.el7_4          
  nss-softokn-freebl.x86_64 0:3.28.3-8.el7_4           nss-softokn-freebl-devel.x86_64 0:3.28.3-8.el7_4                    

Complete!


$ java -version
openjdk version "1.8.0_144"
OpenJDK Runtime Environment (build 1.8.0_144-b01)
OpenJDK 64-Bit Server VM (build 25.144-b01, mixed mode)


