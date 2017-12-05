```sh
$ wget  https://d3kbcqa49mib13.cloudfront.net/spark-2.2.0-bin-hadoop2.7.tgz
--2017-09-18 18:17:16--  https://d3kbcqa49mib13.cloudfront.net/spark-2.2.0-bin-hadoop2.7.tgz
Resolving d3kbcqa49mib13.cloudfront.net (d3kbcqa49mib13.cloudfront.net)... 54.182.1.176, 54.182.1.132, 54.182.1.57, ...
Connecting to d3kbcqa49mib13.cloudfront.net (d3kbcqa49mib13.cloudfront.net)|54.182.1.176|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 203728858 (194M) [application/x-tar]
Saving to: ‘spark-2.2.0-bin-hadoop2.7.tgz’

100%[===================================================>] 203,728,858  224KB/s   in 11m 57s

2017-09-18 18:29:14 (277 KB/s) - ‘spark-2.2.0-bin-hadoop2.7.tgz’ saved [203728858/203728858]

urls: No such file or directory
No URLs found in urls.
FINISHED --2017-09-18 18:29:14--
Total wall clock time: 11m 58s
Downloaded: 1 files, 194M in 11m 57s (277 KB/s)


$ tar zxf spark-2.2.0-bin-hadoop2.7.tgz
$ sudo cp -r spark-2.2.0-bin-hadoop2.7 /usr/local/.
$ cd /usr/local/
$ sudo ln -s spark-2.2.0-bin-hadoop2.7/ spark
$ export SPARK_HOME=/usr/local/spark
$ export PATH=$PATH:$SPARK_HOME/bin
$ ipython
Python 3.6.1 |Continuum Analytics, Inc.| (default, May 11 2017, 13:09:58)
Type 'copyright', 'credits' or 'license' for more information
IPython 6.1.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: import findspark
   ...: findspark.init()
   ...: import pyspark
   ...: import random
   ...: sc = pyspark.SparkContext(appName="Pi")
   ...: num_samples = 100000000
   ...: def inside(p):
   ...:   x, y = random.random(), random.random()
   ...:   return x*x + y*y < 1
   ...: count = sc.parallelize(range(0, num_samples)).filter(inside).count()
   ...: pi = 4 * count / num_samples
   ...: print(pi)
   ...: sc.stop()
   ...:
Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
Setting default log level to "WARN".
To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
17/09/18 18:57:20 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
17/09/18 18:57:21 WARN Utils: Your hostname, localhost.localdomain resolves to a loopback address: 127.0.0.1; using 192.168.200.162 instead (on interface eno1)
17/09/18 18:57:21 WARN Utils: Set SPARK_LOCAL_IP if you need to bind to another address
3.14085248

```


```sh
$ sudo /miniconda3/bin/pip install py4j findspark
```

```sh
$ pyspark
Python 3.6.1 |Continuum Analytics, Inc.| (default, May 11 2017, 13:09:58)
[GCC 4.4.7 20120313 (Red Hat 4.4.7-1)] on linux
Type "help", "copyright", "credits" or "license" for more information.
Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
Setting default log level to "WARN".
To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
17/09/18 18:04:15 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... u                                               sing builtin-java classes where applicable
17/09/18 18:04:15 WARN Utils: Your hostname, localhost.localdomain resolves to a loopback address: 1                                               27.0.0.1; using 192.168.200.162 instead (on interface eno1)
17/09/18 18:04:15 WARN Utils: Set SPARK_LOCAL_IP if you need to bind to another address
17/09/18 18:04:20 WARN ObjectStore: Version information not found in metastore. hive.metastore.schem                                               a.verification is not enabled so recording the schema version 1.2.0
17/09/18 18:04:20 WARN ObjectStore: Failed to get database default, returning NoSuchObjectException
17/09/18 18:04:20 WARN ObjectStore: Failed to get database global_temp, returning NoSuchObjectException
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /__ / .__/\_,_/_/ /_/\_\   version 2.2.0
      /_/

Using Python version 3.6.1 (default, May 11 2017 13:09:58)
SparkSession available as 'spark'.
>>>
```

```sh
$ java -version
openjdk version "1.8.0_144"
OpenJDK Runtime Environment (build 1.8.0_144-b01)
OpenJDK 64-Bit Server VM (build 25.144-b01, mixed mode)
[liangyu@localhost ~]$ cd installFiles/
[liangyu@localhost installFiles]$ wget https://downloads.lightbend.com/scala/2.12.3/scala-2.12.3.rpm
--2017-09-18 20:22:48--  https://downloads.lightbend.com/scala/2.12.3/scala-2.12.3.rpm
Resolving downloads.lightbend.com (downloads.lightbend.com)... 54.182.4.116, 54.182.4.175, 54.182.4.57, ...
Connecting to downloads.lightbend.com (downloads.lightbend.com)|54.182.4.116|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 132498819 (126M) [application/octet-stream]
Saving to: ‘scala-2.12.3.rpm’

100%[========================================================================================================>] 132,498,819 1.23MB/s   in 3m 19s

2017-09-18 20:26:09 (651 KB/s) - ‘scala-2.12.3.rpm’ saved [132498819/132498819]

[liangyu@localhost installFiles]$ sudo rp
rpcbind        rpcgen         rpcinfo        rpc.rquotad    rping          rpmbuild       rpmgraph       rpmsign
rpcclient      rpc.gssd       rpc.mountd     rpc.statd      rpm            rpmdb          rpmkeys        rpmspec
rpcdebug       rpc.idmapd     rpc.nfsd       rpc.svcgssd    rpm2cpio       rpmdumpheader  rpmquery       rpmverify
[liangyu@localhost installFiles]$ sudo rpm -i scala-2.12.3.rpm
[sudo] password for liangyu:
[liangyu@localhost installFiles]$ scala -version
Scala code runner version 2.12.3 -- Copyright 2002-2017, LAMP/EPFL and Lightbend, Inc.


```