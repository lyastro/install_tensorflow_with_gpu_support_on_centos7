# install caffe2 on centos 7

## caffe2 only support python2 at the moment

Based on the guide from https://caffe2.ai/docs/getting-started.html?platform=centos&configuration=cloud

## system
* update yum
```sh
$ sudo yum update
Loaded plugins: fastestmirror, langpacks
base                                                                                        | 3.6 kB  00:00:00     
cuda                                                                                        | 2.5 kB  00:00:00     
epel/x86_64/metalink                                                                        | 5.9 kB  00:00:00     
epel                                                                                        | 4.3 kB  00:00:00     
extras                                                                                      | 3.4 kB  00:00:00     
updates                                                                                     | 3.4 kB  00:00:00     
(1/2): epel/x86_64/updateinfo                                                               | 817 kB  00:00:00     
(2/2): epel/x86_64/primary_db                                                               | 4.8 MB  00:00:01     
Loading mirror speeds from cached hostfile
 * base: mirrors.tuna.tsinghua.edu.cn
 * epel: mirrors.tuna.tsinghua.edu.cn
 * extras: mirrors.neusoft.edu.cn
 * updates: mirrors.btte.net
Resolving Dependencies
--> Running transaction check
---> Package epel-release.noarch 0:7-9 will be updated
---> Package epel-release.noarch 0:7-10 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

===================================================================================================================
 Package                         Arch                      Version                   Repository               Size
===================================================================================================================
Updating:
 epel-release                    noarch                    7-10                      epel                     14 k

Transaction Summary
===================================================================================================================
Upgrade  1 Package

Total download size: 14 k
Is this ok [y/d/N]: y
Downloading packages:
No Presto metadata available for epel
epel-release-7-10.noarch.rpm                                                                |  14 kB  00:00:00     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Updating   : epel-release-7-10.noarch                                                                        1/2 
  Cleanup    : epel-release-7-9.noarch                                                                         2/2 
  Verifying  : epel-release-7-10.noarch                                                                        1/2 
  Verifying  : epel-release-7-9.noarch                                                                         2/2 

Updated:
  epel-release.noarch 0:7-10                                                                                       

Complete!
```

* install Caffe2’s core dependencies

```sh

$ sudo yum install -y \
> automake \
> cmake3 \
> gcc \
> gcc-c++ \
> git \
> kernel-devel \
> leveldb-devel \
> lmdb-devel \
> libtool \
> protobuf-devel \
> python-devel \
> python-pip \
> snappy-devel
Loaded plugins: fastestmirror, langpacks
Loading mirror speeds from cached hostfile
 * base: mirrors.tuna.tsinghua.edu.cn
 * epel: mirrors.tuna.tsinghua.edu.cn
 * extras: mirrors.neusoft.edu.cn
 * updates: mirrors.btte.net
Package automake-1.13.4-3.el7.noarch already installed and latest version
Package gcc-4.8.5-11.el7.x86_64 already installed and latest version
Package gcc-c++-4.8.5-11.el7.x86_64 already installed and latest version
Package git-1.8.3.1-6.el7_2.1.x86_64 already installed and latest version
Package kernel-devel-3.10.0-514.26.2.el7.x86_64 already installed and latest version
Package libtool-2.4.2-22.el7_3.x86_64 already installed and latest version
Package python-devel-2.7.5-48.el7.x86_64 already installed and latest version
Package python2-pip-8.1.2-5.el7.noarch already installed and latest version
Resolving Dependencies
--> Running transaction check
---> Package cmake3.x86_64 0:3.6.3-1.el7 will be installed
--> Processing Dependency: cmake3-data = 3.6.3-1.el7 for package: cmake3-3.6.3-1.el7.x86_64
--> Processing Dependency: libjsoncpp.so.0()(64bit) for package: cmake3-3.6.3-1.el7.x86_64
---> Package leveldb-devel.x86_64 0:1.12.0-11.el7 will be installed
--> Processing Dependency: leveldb(x86-64) = 1.12.0-11.el7 for package: leveldb-devel-1.12.0-11.el7.x86_64
--> Processing Dependency: libleveldb.so.1()(64bit) for package: leveldb-devel-1.12.0-11.el7.x86_64
---> Package lmdb-devel.x86_64 0:0.9.18-1.el7 will be installed
--> Processing Dependency: lmdb(x86-64) = 0.9.18-1.el7 for package: lmdb-devel-0.9.18-1.el7.x86_64
--> Processing Dependency: liblmdb.so.0.0.0()(64bit) for package: lmdb-devel-0.9.18-1.el7.x86_64
---> Package protobuf-devel.x86_64 0:2.5.0-8.el7 will be installed
--> Processing Dependency: protobuf-compiler = 2.5.0-8.el7 for package: protobuf-devel-2.5.0-8.el7.x86_64
--> Processing Dependency: protobuf = 2.5.0-8.el7 for package: protobuf-devel-2.5.0-8.el7.x86_64
--> Processing Dependency: libprotoc.so.8()(64bit) for package: protobuf-devel-2.5.0-8.el7.x86_64
--> Processing Dependency: libprotobuf.so.8()(64bit) for package: protobuf-devel-2.5.0-8.el7.x86_64
---> Package snappy-devel.x86_64 0:1.1.0-3.el7 will be installed
--> Running transaction check
---> Package cmake3-data.noarch 0:3.6.3-1.el7 will be installed
---> Package jsoncpp.x86_64 0:0.10.5-2.el7 will be installed
---> Package leveldb.x86_64 0:1.12.0-11.el7 will be installed
---> Package lmdb.x86_64 0:0.9.18-1.el7 will be installed
---> Package lmdb-libs.x86_64 0:0.9.18-1.el7 will be installed
---> Package protobuf.x86_64 0:2.5.0-8.el7 will be installed
---> Package protobuf-compiler.x86_64 0:2.5.0-8.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

===================================================================================================================
 Package                           Arch                   Version                       Repository            Size
===================================================================================================================
Installing:
 cmake3                            x86_64                 3.6.3-1.el7                   epel                 6.4 M
 leveldb-devel                     x86_64                 1.12.0-11.el7                 epel                  24 k
 lmdb-devel                        x86_64                 0.9.18-1.el7                  epel                  22 k
 protobuf-devel                    x86_64                 2.5.0-8.el7                   base                 163 k
 snappy-devel                      x86_64                 1.1.0-3.el7                   base                  14 k
Installing for dependencies:
 cmake3-data                       noarch                 3.6.3-1.el7                   epel                 1.1 M
 jsoncpp                           x86_64                 0.10.5-2.el7                  epel                  82 k
 leveldb                           x86_64                 1.12.0-11.el7                 epel                 161 k
 lmdb                              x86_64                 0.9.18-1.el7                  epel                  25 k
 lmdb-libs                         x86_64                 0.9.18-1.el7                  epel                  52 k
 protobuf                          x86_64                 2.5.0-8.el7                   base                 338 k
 protobuf-compiler                 x86_64                 2.5.0-8.el7                   base                 261 k

Transaction Summary
===================================================================================================================
Install  5 Packages (+7 Dependent packages)

Total download size: 8.5 M
Installed size: 27 M
Downloading packages:
(1/12): cmake3-3.6.3-1.el7.x86_64.rpm                                                       | 6.4 MB  00:00:05     
(2/12): cmake3-data-3.6.3-1.el7.noarch.rpm                                                  | 1.1 MB  00:00:00     
(3/12): jsoncpp-0.10.5-2.el7.x86_64.rpm                                                     |  82 kB  00:00:00     
(4/12): leveldb-1.12.0-11.el7.x86_64.rpm                                                    | 161 kB  00:00:00     
(5/12): leveldb-devel-1.12.0-11.el7.x86_64.rpm                                              |  24 kB  00:00:00     
(6/12): lmdb-0.9.18-1.el7.x86_64.rpm                                                        |  25 kB  00:00:00     
(7/12): lmdb-devel-0.9.18-1.el7.x86_64.rpm                                                  |  22 kB  00:00:00     
(8/12): lmdb-libs-0.9.18-1.el7.x86_64.rpm                                                   |  52 kB  00:00:00     
(9/12): protobuf-2.5.0-8.el7.x86_64.rpm                                                     | 338 kB  00:00:00     
(10/12): protobuf-compiler-2.5.0-8.el7.x86_64.rpm                                           | 261 kB  00:00:00     
(11/12): snappy-devel-1.1.0-3.el7.x86_64.rpm                                                |  14 kB  00:00:00     
(12/12): protobuf-devel-2.5.0-8.el7.x86_64.rpm                                              | 163 kB  00:00:00     
-------------------------------------------------------------------------------------------------------------------
Total                                                                              1.4 MB/s | 8.5 MB  00:00:05     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : lmdb-libs-0.9.18-1.el7.x86_64                                                                  1/12 
  Installing : protobuf-2.5.0-8.el7.x86_64                                                                    2/12 
  Installing : protobuf-compiler-2.5.0-8.el7.x86_64                                                           3/12 
  Installing : lmdb-0.9.18-1.el7.x86_64                                                                       4/12 
  Installing : leveldb-1.12.0-11.el7.x86_64                                                                   5/12 
  Installing : jsoncpp-0.10.5-2.el7.x86_64                                                                    6/12 
  Installing : cmake3-data-3.6.3-1.el7.noarch                                                                 7/12 
  Installing : cmake3-3.6.3-1.el7.x86_64                                                                      8/12 
  Installing : leveldb-devel-1.12.0-11.el7.x86_64                                                             9/12 
  Installing : lmdb-devel-0.9.18-1.el7.x86_64                                                                10/12 
  Installing : protobuf-devel-2.5.0-8.el7.x86_64                                                             11/12 
  Installing : snappy-devel-1.1.0-3.el7.x86_64                                                               12/12 
  Verifying  : leveldb-devel-1.12.0-11.el7.x86_64                                                             1/12 
  Verifying  : snappy-devel-1.1.0-3.el7.x86_64                                                                2/12 
  Verifying  : jsoncpp-0.10.5-2.el7.x86_64                                                                    3/12 
  Verifying  : lmdb-devel-0.9.18-1.el7.x86_64                                                                 4/12 
  Verifying  : leveldb-1.12.0-11.el7.x86_64                                                                   5/12 
  Verifying  : protobuf-2.5.0-8.el7.x86_64                                                                    6/12 
  Verifying  : protobuf-compiler-2.5.0-8.el7.x86_64                                                           7/12 
  Verifying  : protobuf-devel-2.5.0-8.el7.x86_64                                                              8/12 
  Verifying  : lmdb-libs-0.9.18-1.el7.x86_64                                                                  9/12 
  Verifying  : cmake3-data-3.6.3-1.el7.noarch                                                                10/12 
  Verifying  : lmdb-0.9.18-1.el7.x86_64                                                                      11/12 
  Verifying  : cmake3-3.6.3-1.el7.x86_64                                                                     12/12 

Installed:
  cmake3.x86_64 0:3.6.3-1.el7           leveldb-devel.x86_64 0:1.12.0-11.el7   lmdb-devel.x86_64 0:0.9.18-1.el7  
  protobuf-devel.x86_64 0:2.5.0-8.el7   snappy-devel.x86_64 0:1.1.0-3.el7     

Dependency Installed:
  cmake3-data.noarch 0:3.6.3-1.el7           jsoncpp.x86_64 0:0.10.5-2.el7       leveldb.x86_64 0:1.12.0-11.el7    
  lmdb.x86_64 0:0.9.18-1.el7                 lmdb-libs.x86_64 0:0.9.18-1.el7     protobuf.x86_64 0:2.5.0-8.el7     
  protobuf-compiler.x86_64 0:2.5.0-8.el7    

Complete!

```


* gflags and glog is not found in yum for this version of Linux, so install from source

```sh

$ git clone https://github.com/gflags/gflags.git && \
> cd gflags && \
> mkdir build && cd build && \
> cmake3 -DBUILD_SHARED_LIBS=ON -DCMAKE_CXX_FLAGS='-fPIC' .. && \
> make -j 8 && sudo make install && cd ../.. && \
> git clone https://github.com/google/glog && \
> cd glog && \
> mkdir build && cd build && \
> cmake3 -DBUILD_SHARED_LIBS=ON -DCMAKE_CXX_FLAGS='-fPIC' .. && \
> make -j 8 && sudo make install && cd ../..
Cloning into 'gflags'...
remote: Counting objects: 2209, done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 2209 (delta 3), reused 10 (delta 3), pack-reused 2196
Receiving objects: 100% (2209/2209), 1.46 MiB | 234.00 KiB/s, done.
Resolving deltas: 100% (1274/1274), done.
-- The CXX compiler identification is GNU 4.8.5
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Looking for C++ include unistd.h
-- Looking for C++ include unistd.h - found
-- Looking for C++ include stdint.h
-- Looking for C++ include stdint.h - found
-- Looking for C++ include inttypes.h
-- Looking for C++ include inttypes.h - found
-- Looking for C++ include sys/types.h
-- Looking for C++ include sys/types.h - found
-- Looking for C++ include sys/stat.h
-- Looking for C++ include sys/stat.h - found
-- Looking for C++ include fnmatch.h
-- Looking for C++ include fnmatch.h - found
-- Looking for C++ include stddef.h
-- Looking for C++ include stddef.h - found
-- Check size of uint32_t
-- Check size of uint32_t - done
-- Looking for strtoll
-- Looking for strtoll - found
-- Looking for C++ include pthread.h
-- Looking for C++ include pthread.h - found
-- Looking for pthread_create
-- Looking for pthread_create - not found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE  
-- Check size of pthread_rwlock_t
-- Check size of pthread_rwlock_t - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/XXXXXXXX/github/gflags/build
Scanning dependencies of target gflags_shared
Scanning dependencies of target gflags_nothreads_shared
[ 12%] Building CXX object CMakeFiles/gflags_shared.dir/src/gflags_reporting.cc.o
[ 25%] Building CXX object CMakeFiles/gflags_shared.dir/src/gflags.cc.o
[ 37%] Building CXX object CMakeFiles/gflags_nothreads_shared.dir/src/gflags_reporting.cc.o
[ 62%] Building CXX object CMakeFiles/gflags_nothreads_shared.dir/src/gflags_completions.cc.o
[ 62%] Building CXX object CMakeFiles/gflags_nothreads_shared.dir/src/gflags.cc.o
[ 75%] Building CXX object CMakeFiles/gflags_shared.dir/src/gflags_completions.cc.o
[ 87%] Linking CXX shared library lib/libgflags.so
[100%] Linking CXX shared library lib/libgflags_nothreads.so
[100%] Built target gflags_shared
[100%] Built target gflags_nothreads_shared
[ 50%] Built target gflags_shared
[100%] Built target gflags_nothreads_shared
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/lib/libgflags.so.2.2.1
-- Installing: /usr/local/lib/libgflags.so.2.2
-- Installing: /usr/local/lib/libgflags.so
-- Installing: /usr/local/lib/libgflags_nothreads.so.2.2.1
-- Installing: /usr/local/lib/libgflags_nothreads.so.2.2
-- Installing: /usr/local/lib/libgflags_nothreads.so
-- Installing: /usr/local/include/gflags/gflags.h
-- Installing: /usr/local/include/gflags/gflags_declare.h
-- Installing: /usr/local/include/gflags/gflags_completions.h
-- Installing: /usr/local/include/gflags/gflags_gflags.h
-- Installing: /usr/local/lib/cmake/gflags/gflags-config.cmake
-- Installing: /usr/local/lib/cmake/gflags/gflags-config-version.cmake
-- Installing: /usr/local/lib/cmake/gflags/gflags-targets.cmake
-- Installing: /usr/local/lib/cmake/gflags/gflags-targets-noconfig.cmake
-- Installing: /usr/local/bin/gflags_completions.sh
-- Installing: /usr/local/lib/pkgconfig/gflags.pc
-- Installing: /home/XXXXXXXX/.cmake/packages/gflags/e5f7ce61772240490d3164df06f58ce9
Cloning into 'glog'...
remote: Counting objects: 1720, done.
remote: Total 1720 (delta 0), reused 0 (delta 0), pack-reused 1720
Receiving objects: 100% (1720/1720), 1.45 MiB | 260.00 KiB/s, done.
Resolving deltas: 100% (1229/1229), done.
-- The C compiler identification is GNU 4.8.5
-- The CXX compiler identification is GNU 4.8.5
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Looking for gflags namespace
-- Looking for gflags namespace - gflags
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Looking for pthread_create
-- Looking for pthread_create - not found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE  
-- Looking for dlfcn.h
-- Looking for dlfcn.h - found
-- Looking for execinfo.h
-- Looking for execinfo.h - found
-- Looking for glob.h
-- Looking for glob.h - found
-- Looking for inttypes.h
-- Looking for inttypes.h - found
-- Looking for libunwind.h
-- Looking for libunwind.h - not found
-- Looking for memory.h
-- Looking for memory.h - found
-- Looking for pwd.h
-- Looking for pwd.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stdlib.h
-- Looking for stdlib.h - found
-- Looking for string.h
-- Looking for string.h - found
-- Looking for strings.h
-- Looking for strings.h - found
-- Looking for sys/stat.h
-- Looking for sys/stat.h - found
-- Looking for sys/syscall.h
-- Looking for sys/syscall.h - found
-- Looking for sys/time.h
-- Looking for sys/time.h - found
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for sys/utsname.h
-- Looking for sys/utsname.h - found
-- Looking for syscall.h
-- Looking for syscall.h - found
-- Looking for syslog.h
-- Looking for syslog.h - found
-- Looking for ucontext.h
-- Looking for ucontext.h - found
-- Looking for unistd.h
-- Looking for unistd.h - found
-- Looking for unwind.h
-- Looking for unwind.h - found
-- Looking for C++ include ext/hash_map
-- Looking for C++ include ext/hash_map - found
-- Looking for C++ include ext/hash_set
-- Looking for C++ include ext/hash_set - found
-- Looking for C++ include ext/slist
-- Looking for C++ include ext/slist - found
-- Looking for C++ include tr1/unordered_map
-- Looking for C++ include tr1/unordered_map - found
-- Looking for C++ include tr1/unordered_set
-- Looking for C++ include tr1/unordered_set - found
-- Looking for C++ include unordered_map
-- Looking for C++ include unordered_map - not found
-- Looking for C++ include unordered_set
-- Looking for C++ include unordered_set - not found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of unsigned __int16
-- Check size of unsigned __int16 - failed
-- Check size of u_int16_t
-- Check size of u_int16_t - done
-- Check size of uint16_t
-- Check size of uint16_t - done
-- Looking for dladdr
-- Looking for dladdr - not found
-- Looking for fcntl
-- Looking for fcntl - found
-- Looking for pread
-- Looking for pread - found
-- Looking for pwrite
-- Looking for pwrite - found
-- Looking for sigaction
-- Looking for sigaction - found
-- Looking for sigaltstack
-- Looking for sigaltstack - found
-- Performing Test HAVE_NO_DEPRECATED
-- Performing Test HAVE_NO_DEPRECATED - Success
-- Performing Test HAVE_NO_UNNAMED_TYPE_TEMPLATE_ARGS
-- Performing Test HAVE_NO_UNNAMED_TYPE_TEMPLATE_ARGS - Failed
-- Looking for snprintf
-- Looking for snprintf - found
-- Looking for get_static_proc_name in unwind
-- Looking for get_static_proc_name in unwind - not found
-- Performing Test HAVE___ATTRIBUTE__
-- Performing Test HAVE___ATTRIBUTE__ - Success
-- Performing Test HAVE___ATTRIBUTE__VISIBILITY_DEFAULT
-- Performing Test HAVE___ATTRIBUTE__VISIBILITY_DEFAULT - Success
-- Performing Test HAVE___ATTRIBUTE__VISIBILITY_HIDDEN
-- Performing Test HAVE___ATTRIBUTE__VISIBILITY_HIDDEN - Success
-- Performing Test HAVE___BUILTIN_EXPECT
-- Performing Test HAVE___BUILTIN_EXPECT - Success
-- Performing Test HAVE___SYNC_VAL_COMPARE_AND_SWAP
-- Performing Test HAVE___SYNC_VAL_COMPARE_AND_SWAP - Success
-- Performing Test HAVE_RWLOCK
-- Performing Test HAVE_RWLOCK - Failed
-- Performing Test HAVE___DECLSPEC
-- Performing Test HAVE___DECLSPEC - Failed
-- Performing Test STL_NO_NAMESPACE
-- Performing Test STL_NO_NAMESPACE - Failed
-- Performing Test STL_STD_NAMESPACE
-- Performing Test STL_STD_NAMESPACE - Success
-- Performing Test HAVE_USING_OPERATOR
-- Performing Test HAVE_USING_OPERATOR - Success
-- Performing Test HAVE_NAMESPACES
-- Performing Test HAVE_NAMESPACES - Success
-- Performing Test HAVE_MSVC_TLS
-- Performing Test HAVE_MSVC_TLS - Failed
-- Performing Test HAVE_CXX11_TLS
-- Performing Test HAVE_CXX11_TLS - Failed
-- Performing Test HAVE_CYGWIN_TLS
-- Performing Test HAVE_CYGWIN_TLS - Success
CMake Warning at CMakeLists.txt:612 (export):
  Cannot create package registry file:

    /home/XXXXXXXX/.cmake/packages/glog/8d72bc77012ba9bb1d6fd04180032833

  No such file or directory



-- Configuring done
-- Generating done
-- Build files have been written to: /home/XXXXXXXX/github/glog/build
Scanning dependencies of target glog
[  4%] Building CXX object CMakeFiles/glog.dir/src/logging.cc.o
[  9%] Building CXX object CMakeFiles/glog.dir/src/demangle.cc.o
[ 18%] Building CXX object CMakeFiles/glog.dir/src/vlog_is_on.cc.o
[ 27%] Building CXX object CMakeFiles/glog.dir/src/utilities.cc.o
[ 27%] Building CXX object CMakeFiles/glog.dir/src/raw_logging.cc.o
[ 27%] Building CXX object CMakeFiles/glog.dir/src/symbolize.cc.o
[ 31%] Building CXX object CMakeFiles/glog.dir/src/signalhandler.cc.o
/home/XXXXXXXX/github/glog/src/logging.cc:1153:39: warning: ‘thread’ attribute directive ignored [-Wattributes]
 static GLOG_THREAD_LOCAL_STORAGE bool thread_data_available = true;
                                       ^
/home/XXXXXXXX/github/glog/src/logging.cc:1154:61: warning: ‘thread’ attribute directive ignored [-Wattributes]
 static GLOG_THREAD_LOCAL_STORAGE LogMessage::LogMessageData thread_msg_data;
                                                             ^
[ 36%] Linking CXX shared library libglog.so
[ 36%] Built target glog
Scanning dependencies of target signalhandler_unittest
Scanning dependencies of target stacktrace_unittest
Scanning dependencies of target stl_logging_unittest
Scanning dependencies of target logging_unittest
Scanning dependencies of target symbolize_unittest
Scanning dependencies of target demangle_unittest
Scanning dependencies of target utilities_unittest
[ 40%] Building CXX object CMakeFiles/signalhandler_unittest.dir/src/signalhandler_unittest.cc.o
[ 45%] Building CXX object CMakeFiles/stacktrace_unittest.dir/src/stacktrace_unittest.cc.o
[ 54%] Building CXX object CMakeFiles/utilities_unittest.dir/src/utilities_unittest.cc.o
[ 54%] Building CXX object CMakeFiles/logging_unittest.dir/src/logging_unittest.cc.o
[ 59%] Building CXX object CMakeFiles/stl_logging_unittest.dir/src/stl_logging_unittest.cc.o
[ 63%] Building CXX object CMakeFiles/symbolize_unittest.dir/src/symbolize_unittest.cc.o
[ 68%] Building CXX object CMakeFiles/demangle_unittest.dir/src/demangle_unittest.cc.o
[ 72%] Linking CXX executable stacktrace_unittest
[ 77%] Linking CXX executable signalhandler_unittest
[ 81%] Linking CXX executable symbolize_unittest
[ 81%] Built target signalhandler_unittest
[ 81%] Built target stacktrace_unittest
[ 86%] Linking CXX executable demangle_unittest
[ 86%] Built target symbolize_unittest
[ 90%] Linking CXX executable utilities_unittest
[ 90%] Built target utilities_unittest
[ 90%] Built target demangle_unittest
[ 95%] Linking CXX executable stl_logging_unittest
[ 95%] Built target stl_logging_unittest
[100%] Linking CXX executable logging_unittest
[100%] Built target logging_unittest
[ 36%] Built target glog
[ 45%] Built target signalhandler_unittest
[ 54%] Built target stacktrace_unittest
[ 63%] Built target demangle_unittest
[ 72%] Built target symbolize_unittest
[ 81%] Built target logging_unittest
[ 90%] Built target stl_logging_unittest
[100%] Built target utilities_unittest
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/lib64/libglog.so.0
-- Installing: /usr/local/lib64/libglog.so.0.3.5
-- Installing: /usr/local/lib64/libglog.so
-- Set runtime path of "/usr/local/lib64/libglog.so.0" to ""
-- Installing: /usr/local/include/glog/config.h
-- Installing: /usr/local/include/glog/logging.h
-- Installing: /usr/local/include/glog/raw_logging.h
-- Installing: /usr/local/include/glog/stl_logging.h
-- Installing: /usr/local/include/glog/vlog_is_on.h
-- Installing: /usr/local/include/glog/log_severity.h
-- Installing: /usr/local/lib64/cmake/glog/glog-config.cmake
-- Installing: /usr/local/lib64/cmake/glog/glog-config-version.cmake
-- Installing: /usr/local/lib64/cmake/glog/glog-targets.cmake
-- Installing: /usr/local/lib64/cmake/glog/glog-targets-noconfig.cmake
```

## Python Dependencies#

* Now we need the Python dependencies.

```sh
$ sudo pip2 install \
> flask \
> future \
> graphviz \
> hypothesis \
> jupyter \
> matplotlib \
> numpy \
> protobuf \
> pydot \
> python-nvd3 \
> pyyaml \
> requests \
> scikit-image \
> scipy \
> setuptools \
> six \
> tornado
Collecting flask
  Downloading http://mirrors.aliyun.com/pypi/packages/77/32/e3597cb19ffffe724ad4bf0beca4153419918e7fa4ba6a34b04ee4da3371/Flask-0.12.2-py2.py3-none-any.whl (83kB)
    100% |████████████████████████████████| 92kB 261kB/s 
Collecting future
  Downloading http://mirrors.aliyun.com/pypi/packages/00/2b/8d082ddfed935f3608cc61140df6dcbf0edea1bc3ab52fb6c29ae3e81e85/future-0.16.0.tar.gz (824kB)
    100% |████████████████████████████████| 829kB 358kB/s 
Collecting graphviz
  Downloading http://mirrors.aliyun.com/pypi/packages/9c/f8/a766d4f37c23483b9358fc7d21ee73a4c6ada7361ce88303110fcdfa3ee9/graphviz-0.8-py2.py3-none-any.whl
Collecting hypothesis
  Downloading http://mirrors.aliyun.com/pypi/packages/00/5c/0bb598c4ba88e372869139c1c1e4b76f2ee779226f3f84f1acad23697f60/hypothesis-3.24.1-py2-none-any.whl (160kB)
    100% |████████████████████████████████| 163kB 234kB/s 
Collecting jupyter
  Downloading http://mirrors.aliyun.com/pypi/packages/83/df/0f5dd132200728a86190397e1ea87cd76244e42d39ec5e88efd25b2abd7e/jupyter-1.0.0-py2.py3-none-any.whl
Requirement already satisfied: matplotlib in /usr/lib64/python2.7/site-packages
Requirement already satisfied: numpy in /usr/lib64/python2.7/site-packages
Requirement already satisfied: protobuf in /usr/lib64/python2.7/site-packages
Collecting pydot
  Downloading http://mirrors.aliyun.com/pypi/packages/ae/e6/2c0b7c142c18fb89b294734d45d4264a71269686090af69404df211754c3/pydot-1.2.3.tar.gz
Collecting python-nvd3
  Downloading http://mirrors.aliyun.com/pypi/packages/30/68/5d5d7c1a46de23f1da3b4a7035ac305b76aba582648d19cd9da89b5bd8f6/python-nvd3-0.14.2.tar.gz
Requirement already satisfied: pyyaml in /usr/lib64/python2.7/site-packages
Requirement already satisfied: requests in /usr/lib/python2.7/site-packages
Collecting scikit-image
  Retrying (Retry(total=4, connect=None, read=None, redirect=None)) after connection broken by 'ProtocolError('Connection aborted.', BadStatusLine("''",))': /pypi/simple/scikit-image/
  Downloading http://mirrors.aliyun.com/pypi/packages/39/fa/075d919343ce28219600c05cf3b4494fc5b8b5628c4ad9ba00de75e4c0a7/scikit_image-0.13.0-cp27-cp27mu-manylinux1_x86_64.whl (33.7MB)
    100% |████████████████████████████████| 33.8MB 372kB/s 
Requirement already satisfied: scipy in /usr/lib64/python2.7/site-packages
Requirement already satisfied: setuptools in /usr/lib/python2.7/site-packages
Requirement already satisfied: six in /usr/lib/python2.7/site-packages
Collecting tornado
  Downloading http://mirrors.aliyun.com/pypi/packages/fa/14/52e2072197dd0e63589e875ebf5984c91a027121262aa08f71a49b958359/tornado-4.5.2.tar.gz (483kB)
    100% |████████████████████████████████| 491kB 677kB/s 
Collecting click>=2.0 (from flask)
  Downloading http://mirrors.aliyun.com/pypi/packages/34/c1/8806f99713ddb993c5366c362b2f908f18269f8d792aff1abfd700775a77/click-6.7-py2.py3-none-any.whl (71kB)
    100% |████████████████████████████████| 71kB 102kB/s 
Collecting Jinja2>=2.4 (from flask)
  Downloading http://mirrors.aliyun.com/pypi/packages/5e/73/10c45b82a88ed6b7751bd40da31eeefd7b362e07b56a99aa6e56655a0794/Jinja2-2.9.6-py2.py3-none-any.whl (340kB)
    100% |████████████████████████████████| 348kB 142kB/s 
Requirement already satisfied: Werkzeug>=0.7 in /usr/lib64/python2.7/site-packages (from flask)
Collecting itsdangerous>=0.21 (from flask)
  Downloading http://mirrors.aliyun.com/pypi/packages/dc/b4/a60bcdba945c00f6d608d8975131ab3f25b22f2bcfe1dab221165194b2d4/itsdangerous-0.24.tar.gz (46kB)
    100% |████████████████████████████████| 51kB 79kB/s 
Requirement already satisfied: enum34; python_version == "2.7" in /usr/lib/python2.7/site-packages (from hypothesis)
Collecting ipywidgets (from jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/14/ea/793f6588d5be295d103fb868e26ba8671686b70bd855a21d02302f8dcd37/ipywidgets-7.0.0-py2.py3-none-any.whl (64kB)
    100% |████████████████████████████████| 71kB 112kB/s 
Collecting notebook (from jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/20/13/746be25c0cd02edd65491909cd3bb7c81d5f4ae31107798397962085ec34/notebook-5.0.0-py2.py3-none-any.whl (6.9MB)
    100% |████████████████████████████████| 6.9MB 720kB/s 
Collecting ipykernel (from jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/d8/75/f3e73209d2a9194403655b4e5e4dc0a698b789de31e672cc03afed64d17a/ipykernel-4.6.1-py2-none-any.whl (104kB)
    100% |████████████████████████████████| 112kB 317kB/s 
Collecting qtconsole (from jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/90/ff/047e0dca2627b162866920e7aa93f04523c0ae81e5c67060eec85701992d/qtconsole-4.3.1-py2.py3-none-any.whl (108kB)
    100% |████████████████████████████████| 112kB 282kB/s 
Collecting jupyter-console (from jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/77/82/6469cd7fccf7958cbe5dce2e623f1e3c5e27f1bb1ad36d90519bc2d5d370/jupyter_console-5.2.0-py2.py3-none-any.whl
Collecting nbconvert (from jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/39/ea/280d6c0d92f8e3ca15fd798bbcc2ea141489f9539de7133d8fe10ea4b049/nbconvert-5.3.1-py2.py3-none-any.whl (387kB)
    100% |████████████████████████████████| 389kB 458kB/s 
Requirement already satisfied: pyparsing!=2.0.4,!=2.1.2,!=2.1.6,>=1.5.6 in /usr/lib/python2.7/site-packages (from matplotlib)
Requirement already satisfied: pytz in /usr/lib/python2.7/site-packages (from matplotlib)
Requirement already satisfied: functools32 in /usr/lib/python2.7/site-packages (from matplotlib)
Requirement already satisfied: python-dateutil in /usr/lib/python2.7/site-packages (from matplotlib)
Requirement already satisfied: cycler>=0.10 in /usr/lib/python2.7/site-packages (from matplotlib)
Requirement already satisfied: subprocess32 in /usr/lib64/python2.7/site-packages (from matplotlib)
Collecting python-slugify==1.1.4 (from python-nvd3)
  Downloading http://mirrors.aliyun.com/pypi/packages/2e/13/838ba9b35375ed05bc3b959c81f22ef49e7bdb426063bee888d6f2dc84f0/python-slugify-1.1.4.tar.gz
Collecting networkx>=1.8 (from scikit-image)
  Downloading http://mirrors.aliyun.com/pypi/packages/d3/2c/e473e54afc9fae58dfa97066ef6709a7e35a1dd1c28c5a3842989322be00/networkx-1.11-py2.py3-none-any.whl (1.3MB)
    100% |████████████████████████████████| 1.3MB 487kB/s 
Requirement already satisfied: pillow>=2.1.0 in /usr/lib64/python2.7/site-packages (from scikit-image)
Collecting PyWavelets>=0.4.0 (from scikit-image)
  Downloading http://mirrors.aliyun.com/pypi/packages/3c/84/2346f637fcdc0e89122d6356373a3ee58c27b398dc5880af60eb418a9f5f/PyWavelets-0.5.2-cp27-cp27mu-manylinux1_x86_64.whl (5.6MB)
    100% |████████████████████████████████| 5.7MB 252kB/s 
Requirement already satisfied: backports.ssl_match_hostname in /usr/lib/python2.7/site-packages (from tornado)
Collecting singledispatch (from tornado)
  Downloading http://mirrors.aliyun.com/pypi/packages/c5/10/369f50bcd4621b263927b0a1519987a04383d4a98fb10438042ad410cf88/singledispatch-3.4.0.3-py2.py3-none-any.whl
Collecting certifi (from tornado)
  Downloading http://mirrors.aliyun.com/pypi/packages/40/66/06130724e8205fc8c105db7edb92871c7fff7d31324d7f4405c762624a43/certifi-2017.7.27.1-py2.py3-none-any.whl (349kB)
    100% |████████████████████████████████| 358kB 251kB/s 
Collecting backports_abc>=0.4 (from tornado)
  Downloading http://mirrors.aliyun.com/pypi/packages/7d/56/6f3ac1b816d0cd8994e83d0c4e55bc64567532f7dc543378bd87f81cebc7/backports_abc-0.5-py2.py3-none-any.whl
Collecting MarkupSafe>=0.23 (from Jinja2>=2.4->flask)
  Downloading http://mirrors.aliyun.com/pypi/packages/4d/de/32d741db316d8fdb7680822dd37001ef7a448255de9699ab4bfcbdf4172b/MarkupSafe-1.0.tar.gz
Requirement already satisfied: ipython<6.0.0,>=4.0.0; python_version < "3.3" in /usr/lib/python2.7/site-packages (from ipywidgets->jupyter)
Collecting widgetsnbextension~=3.0.0 (from ipywidgets->jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/a2/04/1377f05763eb7a98d725f87318062aa4aed178305a2db21f5dd026ea1c73/widgetsnbextension-3.0.2-py2.py3-none-any.whl (2.5MB)
    100% |████████████████████████████████| 2.5MB 646kB/s 
Requirement already satisfied: traitlets>=4.3.1 in /usr/lib/python2.7/site-packages (from ipywidgets->jupyter)
Collecting nbformat>=4.2.0 (from ipywidgets->jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/da/27/9a654d2b6cc1eaa517d1c5a4405166c7f6d72f04f6e7eea41855fe808a46/nbformat-4.4.0-py2.py3-none-any.whl (155kB)
    100% |████████████████████████████████| 163kB 359kB/s 
Collecting terminado>=0.3.3; sys_platform != "win32" (from notebook->jupyter)
Collecting jupyter-core (from notebook->jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/48/41/e64f3f38fdb4f7c98814ce93be8b9261068bf0d2ec3550a5ffb492316196/jupyter_core-4.3.0-py2.py3-none-any.whl (76kB)
    100% |████████████████████████████████| 81kB 144kB/s 
Requirement already satisfied: ipython-genutils in /usr/lib/python2.7/site-packages (from notebook->jupyter)
Collecting jupyter-client (from notebook->jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/28/3d/ad981e404f81b44a6e068b53d240414c940cebb92841ca92307dfb67c169/jupyter_client-5.1.0-py2.py3-none-any.whl (84kB)
    100% |████████████████████████████████| 92kB 308kB/s 
Requirement already satisfied: pygments in /usr/lib64/python2.7/site-packages (from qtconsole->jupyter)
Requirement already satisfied: prompt-toolkit<2.0.0,>=1.0.0 in /usr/lib/python2.7/site-packages (from jupyter-console->jupyter)
Requirement already satisfied: bleach in /usr/lib/python2.7/site-packages (from nbconvert->jupyter)
Collecting pandocfilters>=1.4.1 (from nbconvert->jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/4c/ea/236e2584af67bb6df960832731a6e5325fd4441de001767da328c33368ce/pandocfilters-1.4.2.tar.gz
Collecting entrypoints>=0.2.2 (from nbconvert->jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/cc/8b/4eefa9b47f1910b3d2081da67726b066e379b04ca897acfe9f92bac56147/entrypoints-0.2.3-py2.py3-none-any.whl
Collecting testpath (from nbconvert->jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/15/19/d7bc380c479a184e4a5a9ce516e4e2a773165f89b445f7cdced83d94de25/testpath-0.3.1-py2.py3-none-any.whl (161kB)
    100% |████████████████████████████████| 163kB 707kB/s 
Collecting mistune>=0.7.4 (from nbconvert->jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/7b/ab/e71dd1ca31addcd0268c54859eaf75414a10fbc48c79078f7c3066e6ed0d/mistune-0.7.4-py2.py3-none-any.whl
Collecting Unidecode>=0.04.16 (from python-slugify==1.1.4->python-nvd3)
  Downloading http://mirrors.aliyun.com/pypi/packages/01/a1/9d7f3138ee3d79a1ab865a2cb38200ca778d85121db19fe264c76c981184/Unidecode-0.04.21-py2.py3-none-any.whl (228kB)
    100% |████████████████████████████████| 235kB 980kB/s 
Requirement already satisfied: decorator>=3.4.0 in /usr/lib/python2.7/site-packages (from networkx>=1.8->scikit-image)
Requirement already satisfied: olefile in /usr/lib/python2.7/site-packages (from pillow>=2.1.0->scikit-image)
Requirement already satisfied: backports.shutil-get-terminal-size; python_version == "2.7" in /usr/lib/python2.7/site-packages (from ipython<6.0.0,>=4.0.0; python_version < "3.3"->ipywidgets->jupyter)
Requirement already satisfied: simplegeneric>0.8 in /usr/lib/python2.7/site-packages (from ipython<6.0.0,>=4.0.0; python_version < "3.3"->ipywidgets->jupyter)
Requirement already satisfied: pickleshare in /usr/lib/python2.7/site-packages (from ipython<6.0.0,>=4.0.0; python_version < "3.3"->ipywidgets->jupyter)
Requirement already satisfied: pexpect; sys_platform != "win32" in /usr/lib/python2.7/site-packages (from ipython<6.0.0,>=4.0.0; python_version < "3.3"->ipywidgets->jupyter)
Requirement already satisfied: pathlib2; python_version == "2.7" or python_version == "3.3" in /usr/lib/python2.7/site-packages (from ipython<6.0.0,>=4.0.0; python_version < "3.3"->ipywidgets->jupyter)
Collecting jsonschema!=2.5.0,>=2.4 (from nbformat>=4.2.0->ipywidgets->jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/77/de/47e35a97b2b05c2fadbec67d44cfcdcd09b8086951b331d82de90d2912da/jsonschema-2.6.0-py2.py3-none-any.whl
Requirement already satisfied: ptyprocess in /usr/lib/python2.7/site-packages (from terminado>=0.3.3; sys_platform != "win32"->notebook->jupyter)
Collecting pyzmq>=13 (from jupyter-client->notebook->jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/47/5f/98dac82417af5156b49b648ec736bb110884865f31719d84a7593f622d29/pyzmq-16.0.2-cp27-cp27mu-manylinux1_x86_64.whl (3.0MB)
    100% |████████████████████████████████| 3.0MB 1.8MB/s 
Requirement already satisfied: wcwidth in /usr/lib/python2.7/site-packages (from prompt-toolkit<2.0.0,>=1.0.0->jupyter-console->jupyter)
Requirement already satisfied: html5lib!=0.9999,!=0.99999,<0.99999999,>=0.999 in /usr/lib/python2.7/site-packages (from bleach->nbconvert->jupyter)
Collecting configparser>=3.5; python_version == "2.7" (from entrypoints>=0.2.2->nbconvert->jupyter)
  Downloading http://mirrors.aliyun.com/pypi/packages/7c/69/c2ce7e91c89dc073eb1aa74c0621c3eefbffe8216b3f9af9d3885265c01c/configparser-3.5.0.tar.gz
Requirement already satisfied: scandir; python_version < "3.5" in /usr/lib64/python2.7/site-packages (from pathlib2; python_version == "2.7" or python_version == "3.3"->ipython<6.0.0,>=4.0.0; python_version < "3.3"->ipywidgets->jupyter)
Building wheels for collected packages: future, pydot, python-nvd3, tornado, itsdangerous, python-slugify, MarkupSafe, pandocfilters, configparser
  Running setup.py bdist_wheel for future ... done
  Stored in directory: /root/.cache/pip/wheels/e9/52/ba/50c91c0a1a7e2ca55d109ad3083ca093553759b2cf0092267e
  Running setup.py bdist_wheel for pydot ... done
  Stored in directory: /root/.cache/pip/wheels/06/5f/e5/7916847689703a6a696f028fd728739a49ed0a5ed3aef62760
  Running setup.py bdist_wheel for python-nvd3 ... done
  Stored in directory: /root/.cache/pip/wheels/83/5f/2c/33b7a60b61a8e8e5711f6d11f7a8515aea83372f281bcbc0fc
  Running setup.py bdist_wheel for tornado ... done
  Stored in directory: /root/.cache/pip/wheels/91/dc/64/5972fd5dd02b56f361b5018d05d163c956c8c47308abb4086e
  Running setup.py bdist_wheel for itsdangerous ... done
  Stored in directory: /root/.cache/pip/wheels/e2/16/a3/61207804279fe32f620da18ead5649dab8b561d9d474a06610
  Running setup.py bdist_wheel for python-slugify ... done
  Stored in directory: /root/.cache/pip/wheels/af/ae/c8/c19c0e96d3c7e620c2a7bcdf875603c029b8fec411692f5398
  Running setup.py bdist_wheel for MarkupSafe ... done
  Stored in directory: /root/.cache/pip/wheels/37/9a/ed/856deb1b8ef1780641c2cb2083e6bea677d085866b5fa0875f
  Running setup.py bdist_wheel for pandocfilters ... done
  Stored in directory: /root/.cache/pip/wheels/01/da/6f/2528d56d1c5eabe65ae53dab78133b40ceb4094e2516494141
  Running setup.py bdist_wheel for configparser ... done
  Stored in directory: /root/.cache/pip/wheels/6a/ff/6d/ed32bf0c85f8e967b351aa9d0187583e04ea75c2f62567e31c
Successfully built future pydot python-nvd3 tornado itsdangerous python-slugify MarkupSafe pandocfilters configparser
Installing collected packages: click, MarkupSafe, Jinja2, itsdangerous, flask, future, graphviz, hypothesis, singledispatch, certifi, backports-abc, tornado, terminado, jupyter-core, pyzmq, jupyter-client, ipykernel, jsonschema, nbformat, pandocfilters, configparser, entrypoints, testpath, mistune, nbconvert, notebook, widgetsnbextension, ipywidgets, qtconsole, jupyter-console, jupyter, pydot, Unidecode, python-slugify, python-nvd3, networkx, PyWavelets, scikit-image
  Found existing installation: MarkupSafe 0.11
    Uninstalling MarkupSafe-0.11:
      Successfully uninstalled MarkupSafe-0.11
Successfully installed Jinja2-2.9.6 MarkupSafe-1.0 PyWavelets-0.5.2 Unidecode-0.4.21 backports-abc-0.5 certifi-2017.7.27.1 click-6.7 configparser-3.5.0 entrypoints-0.2.3 flask-0.12.2 future-0.16.0 graphviz-0.8 hypothesis-3.24.1 ipykernel-4.6.1 ipywidgets-7.0.0 itsdangerous-0.24 jsonschema-2.6.0 jupyter-1.0.0 jupyter-client-5.1.0 jupyter-console-5.2.0 jupyter-core-4.3.0 mistune-0.7.4 nbconvert-5.3.1 nbformat-4.4.0 networkx-1.11 notebook-5.0.0 pandocfilters-1.4.2 pydot-1.2.3 python-nvd3-0.14.2 python-slugify-1.1.4 pyzmq-16.0.2 qtconsole-4.3.1 scikit-image-0.13.0 singledispatch-3.4.0.3 terminado-0.6 testpath-0.3.1 tornado-4.5.2 widgetsnbextension-3.0.2

```

## compile and install Caffe2 
* Now you need to clone Caffe2 repo and build it (note: update the -j8 with your system’s number of processors; to check this, run nproc from the terminal.):

```sh

$ git clone --recursive https://github.com/caffe2/caffe2
Cloning into 'caffe2'...
remote: Counting objects: 33259, done.
remote: Compressing objects: 100% (64/64), done.
remote: Total 33259 (delta 31), reused 52 (delta 16), pack-reused 33177
Receiving objects: 100% (33259/33259), 146.62 MiB | 2.24 MiB/s, done.
Resolving deltas: 100% (24443/24443), done.
Submodule 'third_party/NNPACK' (https://github.com/Maratyszcza/NNPACK.git) registered for path 'third_party/NNPACK'
Submodule 'third_party/NNPACK_deps/FP16' (https://github.com/Maratyszcza/FP16.git) registered for path 'third_party/NNPACK_deps/FP16'
Submodule 'third_party/NNPACK_deps/FXdiv' (https://github.com/Maratyszcza/FXdiv.git) registered for path 'third_party/NNPACK_deps/FXdiv'
Submodule 'third_party/NNPACK_deps/psimd' (https://github.com/Maratyszcza/psimd.git) registered for path 'third_party/NNPACK_deps/psimd'
Submodule 'third_party/NNPACK_deps/pthreadpool' (https://github.com/Maratyszcza/pthreadpool.git) registered for path 'third_party/NNPACK_deps/pthreadpool'
Submodule 'third_party/android-cmake' (https://github.com/Yangqing/android-cmake.git) registered for path 'third_party/android-cmake'
Submodule 'third_party/benchmark' (https://github.com/google/benchmark.git) registered for path 'third_party/benchmark'
Submodule 'third_party/cub' (https://github.com/NVlabs/cub.git) registered for path 'third_party/cub'
Submodule 'third_party/eigen' (https://github.com/RLovelett/eigen.git) registered for path 'third_party/eigen'
Submodule 'third_party/gloo' (https://github.com/facebookincubator/gloo) registered for path 'third_party/gloo'
Submodule 'third_party/googletest' (https://github.com/google/googletest.git) registered for path 'third_party/googletest'
Submodule 'third_party/ios-cmake' (https://github.com/Yangqing/ios-cmake.git) registered for path 'third_party/ios-cmake'
Submodule 'third_party/nccl' (https://github.com/nvidia/nccl.git) registered for path 'third_party/nccl'
Submodule 'third_party/nervanagpu' (https://github.com/NervanaSystems/nervanagpu.git) registered for path 'third_party/nervanagpu'
Submodule 'third_party/protobuf' (https://github.com/google/protobuf.git) registered for path 'third_party/protobuf'
Submodule 'third_party/pybind11' (https://github.com/pybind/pybind11.git) registered for path 'third_party/pybind11'
Cloning into 'third_party/NNPACK'...
remote: Counting objects: 2241, done.
remote: Total 2241 (delta 0), reused 0 (delta 0), pack-reused 2241
Receiving objects: 100% (2241/2241), 885.07 KiB | 425.00 KiB/s, done.
Resolving deltas: 100% (1492/1492), done.
Submodule path 'third_party/NNPACK': checked out '2695759d3c621f0221209d2e999e66869ca8affb'
Cloning into 'third_party/NNPACK_deps/FP16'...
remote: Counting objects: 203, done.
remote: Total 203 (delta 0), reused 0 (delta 0), pack-reused 203
Receiving objects: 100% (203/203), 92.73 KiB | 126.00 KiB/s, done.
Resolving deltas: 100% (113/113), done.
Submodule path 'third_party/NNPACK_deps/FP16': checked out '2e9eeeb0b463736d13b887d790ac7e72e78fa4bc'
Cloning into 'third_party/NNPACK_deps/FXdiv'...
remote: Counting objects: 159, done.
remote: Total 159 (delta 0), reused 0 (delta 0), pack-reused 159
Receiving objects: 100% (159/159), 22.97 KiB | 0 bytes/s, done.
Resolving deltas: 100% (76/76), done.
Submodule path 'third_party/NNPACK_deps/FXdiv': checked out '8f85044fb41e560508cd69ed26c9afb9cc120e8a'
Cloning into 'third_party/NNPACK_deps/psimd'...
remote: Counting objects: 68, done.
remote: Total 68 (delta 0), reused 0 (delta 0), pack-reused 68
Unpacking objects: 100% (68/68), done.
Submodule path 'third_party/NNPACK_deps/psimd': checked out '0b26a3fb98dd6af7e1f4e0796c56df6b32b1c016'
Cloning into 'third_party/NNPACK_deps/pthreadpool'...
remote: Counting objects: 164, done.
remote: Total 164 (delta 0), reused 0 (delta 0), pack-reused 164
Receiving objects: 100% (164/164), 36.91 KiB | 63.00 KiB/s, done.
Resolving deltas: 100% (70/70), done.
Submodule path 'third_party/NNPACK_deps/pthreadpool': checked out '9e17903a3fc963fe86b151aaddae7cf1b1d34815'
Cloning into 'third_party/android-cmake'...
remote: Counting objects: 742, done.
remote: Total 742 (delta 0), reused 0 (delta 0), pack-reused 742
Receiving objects: 100% (742/742), 239.55 KiB | 203.00 KiB/s, done.
Resolving deltas: 100% (353/353), done.
Submodule path 'third_party/android-cmake': checked out '4c18c932bc18ddbfd55ecf3b1a81bbfb72516ebc'
Cloning into 'third_party/benchmark'...
remote: Counting objects: 3813, done.
remote: Total 3813 (delta 0), reused 0 (delta 0), pack-reused 3813
Receiving objects: 100% (3813/3813), 1014.36 KiB | 214.00 KiB/s, done.
Resolving deltas: 100% (2501/2501), done.
Submodule path 'third_party/benchmark': checked out '4bf28e611b55de8a2d4eece3c335e014f8b0f630'
Cloning into 'third_party/cub'...
remote: Counting objects: 32232, done.
remote: Total 32232 (delta 0), reused 0 (delta 0), pack-reused 32232
Receiving objects: 100% (32232/32232), 16.04 MiB | 29.00 KiB/s, done.
Resolving deltas: 100% (28288/28288), done.
Submodule path 'third_party/cub': checked out 'b20808b1b04ec3d6a625e51fbc1eb76f337754ad'
Cloning into 'third_party/eigen'...
remote: Counting objects: 90371, done.
remote: Compressing objects: 100% (154/154), done.
remote: Total 90371 (delta 216), reused 253 (delta 178), pack-reused 90037
Receiving objects: 100% (90371/90371), 73.12 MiB | 2.35 MiB/s, done.
Resolving deltas: 100% (66900/66900), done.
Submodule path 'third_party/eigen': checked out 'ae9889a130bd0a9d3007f41d015563c2e8ac605f'
Cloning into 'third_party/gloo'...
remote: Counting objects: 1771, done.
remote: Compressing objects: 100% (30/30), done.
remote: Total 1771 (delta 20), reused 22 (delta 16), pack-reused 1725
Receiving objects: 100% (1771/1771), 514.57 KiB | 98.00 KiB/s, done.
Resolving deltas: 100% (1334/1334), done.
Submodule path 'third_party/gloo': checked out 'b52028e4738b2cb948189646ac650f8b8a70f42d'
Submodule 'third-party/googletest' (https://github.com/google/googletest.git) registered for path 'third-party/googletest'
Cloning into 'third-party/googletest'...
remote: Counting objects: 8885, done.
remote: Compressing objects: 100% (20/20), done.
remote: Total 8885 (delta 8), reused 11 (delta 3), pack-reused 8862
Receiving objects: 100% (8885/8885), 2.79 MiB | 500.00 KiB/s, done.
Resolving deltas: 100% (6578/6578), done.
Submodule path 'third_party/gloo/third-party/googletest': checked out 'ec44c6c1675c25b9827aacd08c02433cccde7780'
Cloning into 'third_party/googletest'...
remote: Counting objects: 8885, done.
remote: Compressing objects: 100% (20/20), done.
remote: Total 8885 (delta 8), reused 11 (delta 3), pack-reused 8862
Receiving objects: 100% (8885/8885), 2.79 MiB | 333.00 KiB/s, done.
Resolving deltas: 100% (6578/6578), done.
Submodule path 'third_party/googletest': checked out '5e7fd50e17b6edf1cadff973d0ec68966cf3265e'
Cloning into 'third_party/ios-cmake'...
remote: Counting objects: 225, done.
remote: Total 225 (delta 0), reused 0 (delta 0), pack-reused 225
Receiving objects: 100% (225/225), 52.34 KiB | 47.00 KiB/s, done.
Resolving deltas: 100% (79/79), done.
Submodule path 'third_party/ios-cmake': checked out 'e24081928d9ceec4f4adfcf12293f1e2a20eaedc'
Cloning into 'third_party/nccl'...
remote: Counting objects: 645, done.
remote: Total 645 (delta 0), reused 0 (delta 0), pack-reused 645
Receiving objects: 100% (645/645), 1.37 MiB | 258.00 KiB/s, done.
Resolving deltas: 100% (409/409), done.
Submodule path 'third_party/nccl': checked out '2a974f5ca2aa12b178046b2206b43f1fd69d9fae'
Cloning into 'third_party/nervanagpu'...
remote: Counting objects: 966, done.
remote: Total 966 (delta 0), reused 0 (delta 0), pack-reused 966
Receiving objects: 100% (966/966), 516.63 KiB | 103.00 KiB/s, done.
Resolving deltas: 100% (723/723), done.
Submodule path 'third_party/nervanagpu': checked out 'd4eefd50fbd7d34a17dddbc829888835d67b5f4a'
Cloning into 'third_party/protobuf'...
remote: Counting objects: 46555, done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 46555 (delta 3), reused 3 (delta 1), pack-reused 46548
Receiving objects: 100% (46555/46555), 40.41 MiB | 1.59 MiB/s, done.
Resolving deltas: 100% (31320/31320), done.
Submodule path 'third_party/protobuf': checked out 'a428e42072765993ff674fda72863c9f1aa2d268'
Cloning into 'third_party/pybind11'...
remote: Counting objects: 9184, done.
remote: Compressing objects: 100% (26/26), done.
remote: Total 9184 (delta 12), reused 24 (delta 8), pack-reused 9147
Receiving objects: 100% (9184/9184), 3.34 MiB | 663.00 KiB/s, done.
Resolving deltas: 100% (6184/6184), done.
Submodule path 'third_party/pybind11': checked out 'f38f359f96815421f1780c1a676715efd041f1ae'
Submodule 'tools/clang' (https://github.com/wjakob/clang-cindex-python3) registered for path 'tools/clang'
Cloning into 'tools/clang'...
remote: Counting objects: 353, done.
remote: Total 353 (delta 0), reused 0 (delta 0), pack-reused 353
Receiving objects: 100% (353/353), 119.74 KiB | 57.00 KiB/s, done.
Resolving deltas: 100% (149/149), done.
Submodule path 'third_party/pybind11/tools/clang': checked out '254c7a91e3c6aa254e113197604dafb443f4d429'

```

```
$ cd caffe2 && mkdir build
$ cd build && cmake3 ..
-- Setting CMAKE_FIND_NO_INSTALL_PREFIX
-- The CXX compiler identification is GNU 4.8.5
-- The C compiler identification is GNU 4.8.5
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Build type not set - defaulting to Release
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Looking for pthread_create
-- Looking for pthread_create - not found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE  
-- Found Protobuf: /usr/lib64/libprotobuf.so;-lpthread (found version "2.5.0") 
-- The BLAS backend of choice:Eigen
-- Could NOT find NNPACK (missing:  NNPACK_INCLUDE_DIR NNPACK_LIBRARY PTHREADPOOL_LIBRARY) 
-- Will try to build NNPACK from source. If anything fails, follow the NNPACK prerequisite installation steps.
CMake Warning at cmake/External/nnpack.cmake:155 (message):
  NNPACK is chosen to be installed, but confu and ninja that are needed by it
  are not installed.  As a result we won't build with NNPACK.
Call Stack (most recent call first):
  cmake/Dependencies.cmake:53 (include)
  CMakeLists.txt:79 (include)


CMake Warning at cmake/Dependencies.cmake:58 (message):
  Not compiling with NNPACK.  Suppress this warning with -DUSE_NNPACK=OFF
Call Stack (most recent call first):
  CMakeLists.txt:79 (include)


-- Found GFlags: /usr/local/include  
-- Found gflags  (include: /usr/local/include, library: /usr/local/lib/libgflags.so)
-- Found system gflags install.
-- Found Glog: /usr/local/include  
-- Found glog    (include: /usr/local/include, library: /usr/local/lib64/libglog.so)
-- Found system glog install.
-- Found PythonInterp: /miniconda3/bin/python (found version "3.6.1") 
-- Could NOT find Benchmark (missing:  Benchmark_INCLUDE_DIR Benchmark_LIBRARY) 
-- Found Git: /usr/bin/git (found version "1.8.3.1") 
-- git Version: v0.0.0
-- Version: 0.0.0
-- Performing Test HAVE_CXX_FLAG_STD_CXX11
-- Performing Test HAVE_CXX_FLAG_STD_CXX11 - Success
-- Performing Test HAVE_CXX_FLAG_WALL
-- Performing Test HAVE_CXX_FLAG_WALL - Success
-- Performing Test HAVE_CXX_FLAG_WEXTRA
-- Performing Test HAVE_CXX_FLAG_WEXTRA - Success
-- Performing Test HAVE_CXX_FLAG_WSHADOW
-- Performing Test HAVE_CXX_FLAG_WSHADOW - Success
-- Performing Test HAVE_CXX_FLAG_WERROR
-- Performing Test HAVE_CXX_FLAG_WERROR - Success
-- Performing Test HAVE_CXX_FLAG_PEDANTIC
-- Performing Test HAVE_CXX_FLAG_PEDANTIC - Success
-- Performing Test HAVE_CXX_FLAG_PEDANTIC_ERRORS
-- Performing Test HAVE_CXX_FLAG_PEDANTIC_ERRORS - Success
-- Performing Test HAVE_CXX_FLAG_WSHORTEN_64_TO_32
-- Performing Test HAVE_CXX_FLAG_WSHORTEN_64_TO_32 - Failed
-- Performing Test HAVE_CXX_FLAG_WFLOAT_EQUAL
-- Performing Test HAVE_CXX_FLAG_WFLOAT_EQUAL - Success
-- Performing Test HAVE_CXX_FLAG_FSTRICT_ALIASING
-- Performing Test HAVE_CXX_FLAG_FSTRICT_ALIASING - Success
-- Performing Test HAVE_CXX_FLAG_WZERO_AS_NULL_POINTER_CONSTANT
-- Performing Test HAVE_CXX_FLAG_WZERO_AS_NULL_POINTER_CONSTANT - Success
-- Performing Test HAVE_CXX_FLAG_WSTRICT_ALIASING
-- Performing Test HAVE_CXX_FLAG_WSTRICT_ALIASING - Success
-- Performing Test HAVE_CXX_FLAG_WTHREAD_SAFETY
-- Performing Test HAVE_CXX_FLAG_WTHREAD_SAFETY - Failed
-- Performing Test HAVE_CXX_FLAG_COVERAGE
-- Performing Test HAVE_CXX_FLAG_COVERAGE - Success
-- Performing Test HAVE_STD_REGEX
-- Performing Test HAVE_STD_REGEX -- compiled but failed to run
-- Performing Test HAVE_GNU_POSIX_REGEX
-- Performing Test HAVE_GNU_POSIX_REGEX -- failed to compile
-- Performing Test HAVE_POSIX_REGEX
-- Performing Test HAVE_POSIX_REGEX -- success
-- Performing Test HAVE_STEADY_CLOCK
-- Performing Test HAVE_STEADY_CLOCK -- success
-- Performing Test BENCHMARK_HAS_CXX03_FLAG
-- Performing Test BENCHMARK_HAS_CXX03_FLAG - Success
-- Found LMDB: /usr/include  
-- Found lmdb    (include: /usr/include, library: /usr/lib64/liblmdb.so)
-- Found LevelDB: /usr/include  
-- Found LevelDB (include: /usr/include, library: /usr/lib64/libleveldb.so)
-- Found Snappy: /usr/include  
-- Found Snappy  (include: /usr/include, library: /usr/lib64/libsnappy.so)
-- Could NOT find RocksDB (missing:  RocksDB_INCLUDE_DIR RocksDB_LIBRARIES) 
CMake Warning at cmake/Dependencies.cmake:139 (message):
  Not compiling with RocksDB.  Suppress this warning with -DUSE_ROCKSDB=OFF
Call Stack (most recent call first):
  CMakeLists.txt:79 (include)


CMake Warning at cmake/Dependencies.cmake:182 (message):
  Not compiling with OpenCV.  Suppress this warning with -DUSE_OPENCV=OFF
Call Stack (most recent call first):
  CMakeLists.txt:79 (include)


-- Found PythonInterp: /miniconda3/bin/python (found suitable version "3.6.1", minimum required is "2.7") 
-- Found PythonLibs: /usr/lib64/libpython2.7.so (found suitable version "2.7.5", minimum required is "2.7") 
-- Found NumPy: /miniconda3/lib/python3.6/site-packages/numpy/core/include (found version "1.13.1") 
-- NumPy ver. 1.13.1 found (include: /miniconda3/lib/python3.6/site-packages/numpy/core/include)
-- Could NOT find pybind11 (missing:  pybind11_INCLUDE_DIR) 
-- Could NOT find MPI_C (missing:  MPI_C_LIBRARIES MPI_C_INCLUDE_PATH) 
-- Could NOT find MPI_CXX (missing:  MPI_CXX_LIBRARIES MPI_CXX_INCLUDE_PATH) 
CMake Warning at cmake/Dependencies.cmake:258 (message):
  Not compiling with MPI.  Suppress this warning with -DUSE_MPI=OFF
Call Stack (most recent call first):
  CMakeLists.txt:79 (include)


-- Try OpenMP C flag = [-fopenmp]
-- Performing Test OpenMP_FLAG_DETECTED
-- Performing Test OpenMP_FLAG_DETECTED - Success
-- Try OpenMP CXX flag = [-fopenmp]
-- Performing Test OpenMP_FLAG_DETECTED
-- Performing Test OpenMP_FLAG_DETECTED - Success
-- Found OpenMP: -fopenmp  
-- Adding -fopenmp
-- CUDA detected: 8.0
-- Added CUDA NVCC flags for: sm_61
-- Found libcuda: /usr/lib64/libcuda.so
-- Found libnvrtc: /usr/local/cuda-8.0/lib64/libnvrtc.so
-- Found CUDNN: /usr/local/cuda-8.0/include  
-- Found cuDNN: v6.0.21  (include: /usr/local/cuda-8.0/include, library: /usr/local/cuda-8.0/lib64/libcudnn.so)
-- Could NOT find NCCL (missing:  NCCL_INCLUDE_DIR NCCL_LIBRARY) 
-- NCCL: /home/XXXXXXXX/github/caffe2/third_party/nccl/build/lib/libnccl_static.a
-- Could NOT find CUB (missing:  CUB_INCLUDE_DIR) 
-- Could NOT find Gloo (missing:  Gloo_INCLUDE_DIR Gloo_LIBRARY) 
-- Found CUDA: /usr/local/cuda-8.0 (found suitable version "8.0", minimum required is "7.0") 
-- CUDA detected: 8.0
-- Found libcuda: /usr/lib64/libcuda.so
-- Found libnvrtc: /usr/local/cuda-8.0/lib64/libnvrtc.so
CMake Warning at cmake/Dependencies.cmake:386 (message):
  mobile opengl is only used in android or ios builds.
Call Stack (most recent call first):
  CMakeLists.txt:79 (include)


CMake Warning at cmake/Dependencies.cmake:406 (message):
  Metal is only used in ios builds.
Call Stack (most recent call first):
  CMakeLists.txt:79 (include)


-- Performing Test CAFFE2_LONG_IS_INT32_OR_64
-- Performing Test CAFFE2_LONG_IS_INT32_OR_64 - Success
-- Does not need to define long separately.
-- Performing Test CAFFE2_NEED_TO_TURN_OFF_DEPRECATION_WARNING
-- Performing Test CAFFE2_NEED_TO_TURN_OFF_DEPRECATION_WARNING - Success
-- Performing Test CAFFE2_COMPILER_SUPPORTS_AVX2_EXTENSIONS
-- Performing Test CAFFE2_COMPILER_SUPPORTS_AVX2_EXTENSIONS - Success
-- Current compiler supports avx2 extention. Will build perfkernels.
-- GCC 4.8.5: Adding gcc and gcc_s libs to link line
-- Include NCCL operators
-- Excluding image processing operators due to no opencv
-- Excluding video processing operators due to no opencv
-- Excluding mkl operators as we are not using mkl
-- MPI operators skipped due to no MPI support
-- Automatically generating missing __init__.py files.
-- 
-- ******** Summary ********
-- General:
--   Git version           : 
--   System                : Linux
--   C++ compiler          : /usr/bin/c++
--   C++ compiler version  : 4.8.5
--   Protobuf compiler     : /usr/bin/protoc
--   CXX flags             :  -fopenmp -std=c++11 -O2 -fPIC -Wno-narrowing
--   Build type            : Release
--   Compile definitions   : 
-- 
--   BUILD_BINARY          : ON
--   BUILD_PYTHON          : ON
--     Python version      : 2.7.5
--     Python library      : /usr/lib64/libpython2.7.so
--   BUILD_SHARED_LIBS     : ON
--   BUILD_TEST            : ON
--   USE_CUDA              : ON
--     CUDA version        : 8.0
--     CuDNN version       : 6.0.21
--   USE_FFMPEG            : OFF
--   USE_GFLAGS            : ON
--   USE_GLOG              : ON
--   USE_GLOO              : ON
--   USE_LEVELDB           : ON
--     LevelDB version     : 1.12
--     Snappy version      : 1.1.0
--   USE_LMDB              : ON
--     LMDB version        : 0.9.18
--   USE_METAL             : OFF
--   USE_MOBILE_OPENGL     : OFF
--   USE_MPI               : OFF
--   USE_NCCL              : ON
--   USE_NERVANA_GPU       : OFF
--   USE_NNPACK            : OFF
--   USE_OBSERVERS         : OFF
--   USE_OPENCV            : OFF
--   USE_OPENMP            : ON
--   USE_REDIS             : OFF
--   USE_ROCKSDB           : OFF
--   USE_THREADS           : ON
--   USE_ZMQ               : OFF
-- Configuring done
-- Generating done
-- Build files have been written to: /home/XXXXXXXX/github/caffe2/build
```

```sh
$ sudo make -j8 install
Scanning dependencies of target gmock_main
Scanning dependencies of target gtest
Scanning dependencies of target output_test_helper
Scanning dependencies of target nccl_external
[  0%] Running C++/Python protocol buffer compiler on /home/XXXXXXXX/github/caffe2/caffe/proto/caffe.proto
Scanning dependencies of target gmock
Scanning dependencies of target benchmark
Scanning dependencies of target gloo
[  0%] Creating directories for 'nccl_external'
[  0%] Building CXX object third_party/benchmark/test/CMakeFiles/output_test_helper.dir/output_test_helper.cc.o
[  0%] Building CXX object third_party/googletest/googlemock/gtest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[  0%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/benchmark.cc.o
[  0%] Building CXX object third_party/googletest/googlemock/CMakeFiles/gmock_main.dir/__/googletest/src/gtest-all.cc.o
[  0%] Building CXX object third_party/googletest/googlemock/CMakeFiles/gmock.dir/__/googletest/src/gtest-all.cc.o
[  1%] No download step for 'nccl_external'
[  1%] No patch step for 'nccl_external'
[  1%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/algorithm.cc.o
[  1%] No update step for 'nccl_external'
[  1%] No configure step for 'nccl_external'
Scanning dependencies of target Caffe_PROTO
[  1%] Performing build step for 'nccl_external'
[  1%] Building CXX object caffe/proto/CMakeFiles/Caffe_PROTO.dir/caffe.pb.cc.o
make[3]: warning: jobserver unavailable: using -j1.  Add `+' to parent make rule.
Grabbing  src/nccl.h                          > /home/XXXXXXXX/github/caffe2/third_party/nccl/build/include/nccl.h
Compiling src/libwrap.cu                      > /home/XXXXXXXX/github/caffe2/third_party/nccl/build/obj/libwrap.o
[  1%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/context.cc.o
[  1%] Linking CXX static library liboutput_test_helper.a
[  1%] Built target output_test_helper
[  1%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/benchmark_register.cc.o
[  2%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/common/linux.cc.o
Scanning dependencies of target python_copy_files
[  2%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/common/logging.cc.o
[  2%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/colorprint.cc.o
Compiling src/core.cu                         > /home/XXXXXXXX/github/caffe2/third_party/nccl/build/obj/core.o
[  2%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/commandlineflags.cc.o
[  2%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/rendezvous/context.cc.o
[  2%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/complexity.cc.o
[  3%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/console_reporter.cc.o
[  3%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/rendezvous/file_store.cc.o
[  3%] Built target python_copy_files
[  3%] Running C++/Python protocol buffer compiler on /home/XXXXXXXX/github/caffe2/caffe2/proto/prof_dag.proto
[  3%] Running C++/Python protocol buffer compiler on /home/XXXXXXXX/github/caffe2/caffe2/proto/caffe2.proto
[  3%] Running C++/Python protocol buffer compiler on /home/XXXXXXXX/github/caffe2/caffe2/proto/caffe2_legacy.proto
[  3%] Running C++/Python protocol buffer compiler on /home/XXXXXXXX/github/caffe2/caffe2/proto/hsm.proto
[  4%] Running C++/Python protocol buffer compiler on /home/XXXXXXXX/github/caffe2/caffe2/proto/metanet.proto
[  4%] Running C++/Python protocol buffer compiler on /home/XXXXXXXX/github/caffe2/caffe2/proto/predictor_consts.proto
Scanning dependencies of target Caffe2_PROTO
[  4%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/csv_reporter.cc.o
[  4%] Building CXX object caffe2/proto/CMakeFiles/Caffe2_PROTO.dir/caffe2.pb.cc.o
[  4%] Building CXX object third_party/googletest/googlemock/CMakeFiles/gmock_main.dir/src/gmock-all.cc.o
[  4%] Building CXX object third_party/googletest/googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[  4%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/json_reporter.cc.o
[  4%] Linking CXX shared library libgtest.so
[  4%] Built target gtest
[  4%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/reporter.cc.o
[  4%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/rendezvous/hash_store.cc.o
Scanning dependencies of target gtest_main
[  5%] Building CXX object third_party/googletest/googlemock/gtest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
Compiling src/all_gather.cu                   > /home/XXXXXXXX/github/caffe2/third_party/nccl/build/obj/all_gather.o
[  5%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/sleep.cc.o
[  5%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/string_util.cc.o
[  5%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/rendezvous/prefix_store.cc.o
[  5%] Linking CXX shared library libgtest_main.so
[  5%] Built target gtest_main
[  6%] Building CXX object third_party/googletest/googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[  7%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/sysinfo.cc.o
[  8%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/rendezvous/store.cc.o
[  8%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/transport/address.cc.o
[  8%] Building CXX object third_party/benchmark/src/CMakeFiles/benchmark.dir/timers.cc.o
[  8%] Building CXX object caffe2/proto/CMakeFiles/Caffe2_PROTO.dir/caffe2_legacy.pb.cc.o
[  8%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/transport/buffer.cc.o
[  8%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/transport/device.cc.o
[  8%] Linking CXX shared library libbenchmark.so
[  8%] Built target benchmark
[  8%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/transport/pair.cc.o
[  8%] Linking CXX shared library libgmock.so
[  8%] Built target gmock
[  8%] Building CXX object caffe2/proto/CMakeFiles/Caffe2_PROTO.dir/hsm.pb.cc.o
[  9%] Building CXX object caffe2/proto/CMakeFiles/Caffe2_PROTO.dir/metanet.pb.cc.o
[  9%] Linking CXX shared library libgmock_main.so
[  9%] Built target gmock_main
Scanning dependencies of target reporter_output_test
[  9%] Building CXX object third_party/benchmark/test/CMakeFiles/reporter_output_test.dir/reporter_output_test.cc.o
[  9%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/transport/tcp/address.cc.o
[ 10%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/transport/tcp/buffer.cc.o
Scanning dependencies of target multiple_ranges_test
[ 10%] Building CXX object third_party/benchmark/test/CMakeFiles/multiple_ranges_test.dir/multiple_ranges_test.cc.o
[ 10%] Building CXX object caffe2/proto/CMakeFiles/Caffe2_PROTO.dir/predictor_consts.pb.cc.o
[ 11%] Linking CXX executable reporter_output_test
[ 11%] Built target reporter_output_test
Scanning dependencies of target cxx03_test
[ 11%] Building CXX object third_party/benchmark/test/CMakeFiles/cxx03_test.dir/cxx03_test.cc.o
[ 11%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/transport/tcp/device.cc.o
[ 11%] Linking CXX executable multiple_ranges_test
[ 11%] Built target multiple_ranges_test
Scanning dependencies of target map_test
[ 11%] Linking CXX executable cxx03_test
[ 11%] Building CXX object third_party/benchmark/test/CMakeFiles/map_test.dir/map_test.cc.o
[ 11%] Built target cxx03_test
Scanning dependencies of target benchmark_test
[ 11%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo.dir/transport/tcp/pair.cc.o
[ 11%] Building CXX object third_party/benchmark/test/CMakeFiles/benchmark_test.dir/benchmark_test.cc.o
[ 11%] Linking CXX executable map_test
[ 11%] Building CXX object caffe2/proto/CMakeFiles/Caffe2_PROTO.dir/prof_dag.pb.cc.o
[ 11%] Built target map_test
Scanning dependencies of target basic_test
[ 11%] Building CXX object third_party/benchmark/test/CMakeFiles/basic_test.dir/basic_test.cc.o
Scanning dependencies of target complexity_test
[ 11%] Building CXX object third_party/benchmark/test/CMakeFiles/complexity_test.dir/complexity_test.cc.o
[ 12%] Linking CXX executable basic_test
[ 12%] Built target basic_test
Scanning dependencies of target diagnostics_test
[ 12%] Building CXX object third_party/benchmark/test/CMakeFiles/diagnostics_test.dir/diagnostics_test.cc.o
[ 12%] Linking CXX executable benchmark_test
Scanning dependencies of target options_test
[ 13%] Building CXX object third_party/benchmark/test/CMakeFiles/options_test.dir/options_test.cc.o
[ 13%] Built target benchmark_test
Scanning dependencies of target skip_with_error_test
[ 13%] Building CXX object third_party/benchmark/test/CMakeFiles/skip_with_error_test.dir/skip_with_error_test.cc.o
[ 13%] Linking CXX executable diagnostics_test
[ 13%] Built target diagnostics_test
Scanning dependencies of target fixture_test
[ 13%] Building CXX object third_party/benchmark/test/CMakeFiles/fixture_test.dir/fixture_test.cc.o
[ 13%] Built target Caffe2_PROTO
Scanning dependencies of target donotoptimize_test
[ 13%] Building CXX object third_party/benchmark/test/CMakeFiles/donotoptimize_test.dir/donotoptimize_test.cc.o
[ 13%] Linking CXX executable complexity_test
[ 13%] Linking CXX executable options_test
[ 13%] Built target complexity_test
Scanning dependencies of target filter_test
[ 13%] Built target options_test
[ 13%] Building CXX object third_party/benchmark/test/CMakeFiles/filter_test.dir/filter_test.cc.o
Scanning dependencies of target register_benchmark_test
[ 13%] Building CXX object third_party/benchmark/test/CMakeFiles/register_benchmark_test.dir/register_benchmark_test.cc.o
[ 13%] Linking CXX static library libgloo.a
[ 13%] Built target gloo
[ 13%] Linking CXX executable donotoptimize_test
[ 13%] Linking CXX executable fixture_test
[ 13%] Built target donotoptimize_test
[ 13%] Linking CXX executable skip_with_error_test
[ 13%] Built target fixture_test
[ 13%] Built target skip_with_error_test
[ 14%] Linking CXX executable filter_test
[ 14%] Built target filter_test
[ 14%] Linking CXX executable register_benchmark_test
[ 14%] Built target register_benchmark_test
[ 14%] Built target Caffe_PROTO
Scanning dependencies of target Caffe2_perfkernels_avx
Scanning dependencies of target Caffe2_perfkernels_avx2
[ 14%] Building CXX object caffe2/perfkernels/CMakeFiles/Caffe2_perfkernels_avx.dir/common_avx.cc.o
[ 14%] Building CXX object caffe2/perfkernels/CMakeFiles/Caffe2_perfkernels_avx.dir/typed_axpy_avx.cc.o
[ 15%] Building CXX object caffe2/perfkernels/CMakeFiles/Caffe2_perfkernels_avx2.dir/common_avx2.cc.o
[ 15%] Building CXX object caffe2/perfkernels/CMakeFiles/Caffe2_perfkernels_avx2.dir/embedding_lookup_avx2.cc.o
[ 15%] Building CXX object caffe2/perfkernels/CMakeFiles/Caffe2_perfkernels_avx2.dir/typed_axpy_avx2.cc.o
[ 15%] Built target Caffe2_perfkernels_avx
[ 15%] Built target Caffe2_perfkernels_avx2
Compiling src/all_reduce.cu                   > /home/XXXXXXXX/github/caffe2/third_party/nccl/build/obj/all_reduce.o
Compiling src/broadcast.cu                    > /home/XXXXXXXX/github/caffe2/third_party/nccl/build/obj/broadcast.o
Compiling src/reduce.cu                       > /home/XXXXXXXX/github/caffe2/third_party/nccl/build/obj/reduce.o
Compiling src/reduce_scatter.cu               > /home/XXXXXXXX/github/caffe2/third_party/nccl/build/obj/reduce_scatter.o
Linking   libnccl.so.1.3.2                    > /home/XXXXXXXX/github/caffe2/third_party/nccl/build/lib/libnccl.so.1.3.2
Archiving libnccl_static.a                    > /home/XXXXXXXX/github/caffe2/third_party/nccl/build/lib/libnccl_static.a
[ 15%] No install step for 'nccl_external'
[ 15%] Completed 'nccl_external'
[ 15%] Built target nccl_external
[ 15%] Building NVCC (Device) object third_party/gloo/gloo/CMakeFiles/gloo_cuda.dir/gloo_cuda_generated_cuda.cu.o
[ 16%] Building NVCC (Device) object third_party/gloo/gloo/CMakeFiles/gloo_cuda.dir/nccl/gloo_cuda_generated_nccl.cu.o
[ 16%] Building NVCC (Device) object third_party/gloo/gloo/CMakeFiles/gloo_cuda.dir/gloo_cuda_generated_cuda_private.cu.o
Scanning dependencies of target gloo_cuda
[ 16%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo_cuda.dir/cuda_allreduce_halving_doubling.cc.o
[ 16%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo_cuda.dir/cuda_broadcast_one_to_all.cc.o
[ 16%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo_cuda.dir/cuda_allreduce_ring.cc.o
[ 16%] Building CXX object third_party/gloo/gloo/CMakeFiles/gloo_cuda.dir/cuda_allreduce_ring_chunked.cc.o
[ 17%] Linking CXX static library libgloo_cuda.a
[ 17%] Built target gloo_cuda
Scanning dependencies of target Caffe2_CPU
[ 17%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/contrib/gloo/common.cc.o
[ 17%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/contrib/gloo/broadcast_ops.cc.o
[ 17%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/contrib/gloo/allreduce_ops.cc.o
[ 17%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/contrib/gloo/barrier_ops.cc.o
[ 17%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/allocator.cc.o
[ 18%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/contrib/gloo/context.cc.o
[ 18%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/contrib/gloo/common_world_ops.cc.o
[ 18%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/contrib/gloo/store_handler.cc.o
[ 18%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/blob_serialization.cc.o
[ 18%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/blob_stats.cc.o
[ 18%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/common.cc.o
[ 19%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/db.cc.o
[ 19%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/event.cc.o
[ 19%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/flags.cc.o
[ 19%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/graph.cc.o
[ 19%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/init.cc.o
[ 19%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/init_omp.cc.o
[ 20%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/logging.cc.o
[ 20%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/memonger.cc.o
[ 20%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/net.cc.o
[ 20%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/net_dag.cc.o
[ 20%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/net_simple.cc.o
[ 21%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/operator.cc.o
[ 21%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/operator_schema.cc.o
[ 21%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/plan_executor.cc.o
[ 21%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/predictor.cc.o
[ 21%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/qtensor.cc.o
[ 21%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/qtensor_serialization.cc.o
[ 22%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/stats.cc.o
[ 22%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/tensor.cc.o
[ 22%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/transform.cc.o
[ 22%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/typeid.cc.o
[ 22%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/types.cc.o
[ 22%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/core/workspace.cc.o
[ 23%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/db/create_db_op.cc.o
[ 23%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/db/protodb.cc.o
[ 23%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/db/lmdb.cc.o
[ 23%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/db/leveldb.cc.o
[ 23%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/distributed/file_store_handler.cc.o
[ 23%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/distributed/file_store_handler_op.cc.o
[ 24%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/distributed/store_handler.cc.o
[ 24%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/distributed/store_ops.cc.o
[ 24%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/abs_op.cc.o
[ 24%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/accumulate_op.cc.o
[ 24%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/accuracy_op.cc.o
[ 25%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/apmeter_op.cc.o
[ 25%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/atomic_ops.cc.o
[ 25%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/batch_box_cox_op.cc.o
[ 25%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/batch_gather_ops.cc.o
[ 25%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/batch_matmul_op.cc.o
[ 25%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/boolean_mask_ops.cc.o
[ 26%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/boolean_unmask_ops.cc.o
[ 26%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/cast_op.cc.o
[ 26%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/channel_shuffle_op.cc.o
[ 26%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/clip_op.cc.o
[ 26%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/communicator_op.cc.o
[ 26%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/concat_split_op.cc.o
[ 27%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/conditional_op.cc.o
[ 27%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/conv_gradient_op.cc.o
[ 27%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/conv_op.cc.o
[ 27%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/conv_op_eigen.cc.o
[ 27%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/conv_op_shared.cc.o
[ 27%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/conv_transpose_gradient_op.cc.o
[ 28%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/conv_transpose_op.cc.o
[ 28%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/conv_transpose_op_mobile.cc.o
[ 28%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/cos_op.cc.o
[ 28%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/cosine_embedding_criterion_op.cc.o
[ 28%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/counter_ops.cc.o
[ 29%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/cross_entropy_op.cc.o
[ 29%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/dataset_ops.cc.o
[ 29%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/distance_op.cc.o
[ 29%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/do_op.cc.o
[ 29%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/dropout_op.cc.o
[ 29%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/elementwise_add_op.cc.o
[ 30%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/elementwise_div_op.cc.o
[ 30%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/elementwise_linear_op.cc.o
[ 30%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/elementwise_logical_ops.cc.o
[ 30%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/elementwise_mul_op.cc.o
[ 30%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/elementwise_op.cc.o
[ 30%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/elementwise_op_schema.cc.o
[ 31%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/elementwise_sub_op.cc.o
[ 31%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/elementwise_sum_op.cc.o
[ 31%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/elu_op.cc.o
[ 31%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/exp_op.cc.o
[ 31%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/extend_tensor_op.cc.o
[ 31%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/feed_blob_op.cc.o
[ 32%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/filler_op.cc.o
[ 32%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/find_duplicate_elements_op.cc.o
[ 32%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/find_op.cc.o
[ 32%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/free_op.cc.o
[ 32%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/fully_connected_op.cc.o
[ 33%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/given_tensor_fill_op.cc.o
[ 33%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/gru_unit_op.cc.o
[ 33%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/h_softmax_op.cc.o
[ 33%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/half_float_ops.cc.o
[ 33%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/if_op.cc.o
[ 33%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/im2col_op.cc.o
[ 34%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/index_hash_ops.cc.o
[ 34%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/index_ops.cc.o
[ 34%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/instance_norm_gradient_op.cc.o
[ 34%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/instance_norm_op.cc.o
[ 34%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/last_n_window_collector.cc.o
[ 34%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/layer_norm_op.cc.o
[ 35%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/leaky_relu_op.cc.o
[ 35%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/lengths_reducer_ops.cc.o
[ 35%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/lengths_reducer_rowwise_8bit_ops.cc.o
[ 35%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/lengths_tile_op.cc.o
[ 35%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/lengths_top_k_op.cc.o
[ 35%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/load_save_op.cc.o
[ 36%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/local_response_normalization_op.cc.o
[ 36%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/log_op.cc.o
[ 36%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/logit_op.cc.o
[ 36%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/loss_op.cc.o
[ 36%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/lp_pool_op.cc.o
[ 37%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/lpnorm_op.cc.o
[ 37%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/lstm_unit_op.cc.o
[ 37%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/map_ops.cc.o
[ 37%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/margin_ranking_criterion_op.cc.o
[ 37%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/math_ops.cc.o
[ 37%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/matmul_op.cc.o
[ 38%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/merge_id_lists_op.cc.o
[ 38%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/multi_class_accuracy_op.cc.o
[ 38%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/negative_op.cc.o
[ 38%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/normalize_op.cc.o
[ 38%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/one_hot_ops.cc.o
[ 38%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/order_switch_ops.cc.o
[ 39%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/pack_rnn_sequence_op.cc.o
[ 39%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/pack_segments.cc.o
[ 39%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/pad_op.cc.o
[ 39%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/partition_ops.cc.o
[ 39%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/perplexity_op.cc.o
[ 39%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/piecewise_linear_transform_op.cc.o
[ 40%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/pool_gradient_op.cc.o
[ 40%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/pool_op.cc.o
[ 40%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/prelu_op.cc.o
[ 40%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/prepend_dim_op.cc.o
[ 40%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/rank_loss_op.cc.o
[ 41%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/recurrent_network_blob_fetcher_op.cc.o
[ 41%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/recurrent_network_executor.cc.o
[ 41%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/recurrent_network_op.cc.o
[ 41%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/reduction_ops.cc.o
[ 41%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/relu_op.cc.o
[ 41%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/remove_data_blocks_op.cc.o
[ 42%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/replace_nan_op.cc.o
[ 42%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/reservoir_sampling.cc.o
[ 42%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/reshape_op.cc.o
[ 42%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/resize_op.cc.o
[ 42%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/reverse_packed_segs_op.cc.o
[ 42%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/roi_pool_op.cc.o
[ 43%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/rowmul_op.cc.o
[ 43%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/scale_op.cc.o
[ 43%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/segment_reduction_op.cc.o
[ 43%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/sequence_ops.cc.o
[ 43%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/shape_op.cc.o
[ 44%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/sigmoid_op.cc.o
[ 44%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/sin_op.cc.o
[ 44%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/sinusoid_position_encoding_op.cc.o
[ 44%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/slice_op.cc.o
[ 44%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/softmax_op.cc.o
[ 44%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/softmax_shared.cc.o
[ 45%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/softmax_with_loss_op.cc.o
[ 45%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/softplus_op.cc.o
[ 45%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/softsign_op.cc.o
[ 45%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/space_batch_op.cc.o
[ 45%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/sparse_to_dense_mask_op.cc.o
[ 45%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/sparse_to_dense_op.cc.o
[ 46%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/spatial_batch_norm_gradient_op.cc.o
[ 46%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/spatial_batch_norm_op.cc.o
[ 46%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/spatial_softmax_with_loss_op.cc.o
[ 46%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/square_root_divide_op.cc.o
[ 46%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/stats_ops.cc.o
[ 46%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/stop_gradient.cc.o
[ 47%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/string_ops.cc.o
[ 47%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/summarize_op.cc.o
[ 47%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/tanh_op.cc.o
[ 47%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/tensor_protos_db_input.cc.o
[ 47%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/text_file_reader.cc.o
[ 48%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/text_file_reader_utils.cc.o
[ 48%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/tile_op.cc.o
[ 48%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/top_k.cc.o
[ 48%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/transpose_op.cc.o
[ 48%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/tt_linear_op.cc.o
[ 48%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/utility_ops.cc.o
[ 49%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/while_op.cc.o
[ 49%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/workspace_ops.cc.o
[ 49%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/operators/zero_gradient_op.cc.o
[ 49%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/perfkernels/embedding_lookup.cc.o
[ 49%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/perfkernels/typed_axpy.cc.o
[ 49%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/queue/blobs_queue.cc.o
[ 50%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/queue/blobs_queue_db.cc.o
[ 50%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/queue/queue_ops.cc.o
[ 50%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/queue/rebatching_queue.cc.o
[ 50%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/queue/rebatching_queue_ops.cc.o
[ 50%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/sgd/adagrad_op.cc.o
[ 50%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/sgd/adam_op.cc.o
[ 51%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/sgd/ftrl_op.cc.o
[ 51%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/sgd/iter_op.cc.o
[ 51%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/sgd/learning_rate_op.cc.o
[ 51%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/sgd/momentum_sgd_op.cc.o
[ 51%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/sgd/rmsprop_op.cc.o
[ 52%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/sgd/yellowfin_op.cc.o
[ 52%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/transforms/common_subexpression_elimination.cc.o
[ 52%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/transforms/conv_to_nnpack_transform.cc.o
[ 52%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/transforms/pattern_net_transform.cc.o
[ 52%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/transforms/single_op_transform.cc.o
[ 52%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/utils/cpuid.cc.o
[ 53%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/utils/math_cpu.cc.o
[ 53%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/utils/murmur_hash3.cc.o
[ 53%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/utils/proto_utils.cc.o
[ 53%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/utils/signal_handler.cc.o
[ 53%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/utils/smart_tensor_printer.cc.o
[ 53%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/utils/string_utils.cc.o
[ 54%] Building CXX object caffe2/CMakeFiles/Caffe2_CPU.dir/utils/threadpool/ThreadPool.cc.o
[ 54%] Linking CXX shared library libCaffe2_CPU.so
[ 54%] Built target Caffe2_CPU
[ 54%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/utils/Caffe2_GPU_generated_math_gpu.cu.o
[ 54%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/core/Caffe2_GPU_generated_context_gpu.cu.o
[ 54%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_abs_op.cu.o
[ 54%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_batch_matmul_op.cu.o
[ 54%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_boolean_mask_ops.cu.o
[ 55%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_batch_gather_ops.cu.o
[ 55%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_accuracy_op.cu.o
[ 55%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_accumulate_op.cu.o
[ 55%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_boolean_unmask_ops.cu.o
[ 55%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_cast_op.cu.o
[ 56%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_channel_shuffle_op_gpu.cu.o
[ 56%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_cos_op.cu.o
[ 56%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_clip_op.cu.o
[ 56%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_cosine_embedding_criterion_op.cu.o
[ 56%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_cross_entropy_op.cu.o
[ 56%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_distance_op.cu.o
[ 57%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_dropout_op.cu.o
[ 57%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_elementwise_linear_op.cu.o
[ 57%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_elementwise_op.cu.o
[ 57%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_elu_op.cu.o
[ 57%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_exp_op.cu.o
[ 57%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_filler_op.cu.o
[ 58%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_find_op.cu.o
[ 58%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_given_tensor_fill_op.cu.o
[ 58%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_gru_unit_op_gpu.cu.o
[ 58%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_half_float_ops.cu.o
[ 58%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_instance_norm_op.cu.o
[ 58%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_layer_norm_op.cu.o
[ 59%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_leaky_relu_op.cu.o
[ 59%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_local_response_normalization_op.cu.o
[ 59%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_log_op.cu.o
[ 59%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_loss_op.cu.o
[ 59%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_lp_pool_op.cu.o
[ 60%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_lstm_unit_op_gpu.cu.o
[ 60%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_margin_ranking_criterion_op.cu.o
/home/XXXXXXXX/github/caffe2/caffe2/operators/layer_norm_op.cu: In member function ‘bool caffe2::LayerNormGradientOp<Context>::DoRunWithType() [with T = float; Context = caffe2::CUDAContext]’:
/home/XXXXXXXX/github/caffe2/caffe2/operators/layer_norm_op.cu:264:60: warning: narrowing conversion of ‘(int)left’ from ‘int’ to ‘long unsigned int’ inside { } [-Wnarrowing]
   gscratch_.Resize(std::vector<size_t>{left, right});
                                                            ^
/home/XXXXXXXX/github/caffe2/caffe2/operators/layer_norm_op.cu:264:60: warning: narrowing conversion of ‘left’ from ‘const int’ to ‘long unsigned int’ inside { } [-Wnarrowing]
/home/XXXXXXXX/github/caffe2/caffe2/operators/layer_norm_op.cu:264:60: warning: narrowing conversion of ‘(int)right’ from ‘int’ to ‘long unsigned int’ inside { } [-Wnarrowing]
/home/XXXXXXXX/github/caffe2/caffe2/operators/layer_norm_op.cu:264:60: warning: narrowing conversion of ‘right’ from ‘const int’ to ‘long unsigned int’ inside { } [-Wnarrowing]
/home/XXXXXXXX/github/caffe2/caffe2/operators/layer_norm_op.cu:294:56: warning: narrowing conversion of ‘(int)left’ from ‘int’ to ‘long unsigned int’ inside { } [-Wnarrowing]
   dstdev_.Resize(vector<size_t>{left, 1});
                                                        ^
/home/XXXXXXXX/github/caffe2/caffe2/operators/layer_norm_op.cu:294:56: warning: narrowing conversion of ‘left’ from ‘const int’ to ‘long unsigned int’ inside { } [-Wnarrowing]
[ 60%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_math_ops.cu.o
[ 60%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_max_pool_with_index.cu.o
/home/XXXXXXXX/github/caffe2/caffe2/operators/lp_pool_op.cu(24): warning: function "caffe2::<unnamed>::cuda_pow(T, T) [with T=double]" was declared but never referenced

/home/XXXXXXXX/github/caffe2/caffe2/operators/lp_pool_op.cu(33): warning: function "caffe2::<unnamed>::cuda_abs(T) [with T=double]" was declared but never referenced

[ 60%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_mem_query_op.cu.o
[ 60%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_multi_class_accuracy_op.cu.o
[ 61%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_negative_op.cu.o
[ 61%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_normalize_op.cu.o
[ 61%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_one_hot_ops.cu.o
[ 61%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_order_switch_ops.cu.o
[ 61%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_pad_op_gpu.cu.o
[ 61%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_perplexity_op.cu.o
[ 62%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_piecewise_linear_transform_op.cu.o
[ 62%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_pool_op.cu.o
[ 62%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_pool_op_cudnn.cu.o
[ 62%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_prelu_op.cu.o
[ 62%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_reduction_ops.cu.o
[ 62%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_relu_op.cu.o
[ 63%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_relu_op_fp16.cu.o
[ 63%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_resize_op.cu.o
[ 63%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_reverse_packed_segs_op.cu.o
[ 63%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_roi_pool_op.cu.o
[ 63%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_segment_reduction_op_gpu.cu.o
[ 64%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_sigmoid_op.cu.o
[ 64%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_sin_op.cu.o
[ 64%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_slice_op.cu.o
[ 64%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_softmax_ops.cu.o
[ 64%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_softplus_op.cu.o
[ 64%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_softsign_op.cu.o
[ 65%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_space_batch_op_gpu.cu.o
[ 65%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_sparse_to_dense_op.cu.o
[ 65%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_summarize_op.cu.o
[ 65%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_tanh_op.cu.o
[ 65%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_tile_op.cu.o
[ 65%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_top_k.cu.o
[ 66%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_transpose_op.cu.o
[ 66%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/Caffe2_GPU_generated_utility_ops.cu.o
[ 66%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/sgd/Caffe2_GPU_generated_adagrad_op_gpu.cu.o
[ 66%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/sgd/Caffe2_GPU_generated_adam_op_gpu.cu.o
[ 66%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/sgd/Caffe2_GPU_generated_momentum_sgd_op_gpu.cu.o
[ 67%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/sgd/Caffe2_GPU_generated_rmsprop_op_gpu.cu.o
[ 67%] Building NVCC (Device) object caffe2/CMakeFiles/Caffe2_GPU.dir/sgd/Caffe2_GPU_generated_yellowfin_op_gpu.cu.o
Scanning dependencies of target Caffe2_GPU
[ 67%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/contrib/gloo/common_world_ops_gpu.cc.o
[ 67%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/contrib/gloo/broadcast_ops_gpu.cc.o
[ 67%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/contrib/gloo/allreduce_ops_gpu.cc.o
[ 67%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/core/common_gpu.cc.o
[ 67%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/contrib/nccl/cuda_nccl_op_gpu.cc.o
[ 67%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/core/common_cudnn.cc.o
[ 68%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/contrib/nccl/cuda_nccl_gpu.cc.o
[ 68%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/core/blob_serialization_gpu.cc.o
[ 68%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/core/event_gpu.cc.o
[ 69%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/core/net_async_dag_gpu.cc.o
[ 69%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/core/net_singlethread_async_gpu.cc.o
[ 69%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/cuda_rtc/elemenntwise_rtc_gpu.cc.o
[ 69%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/cuda_rtc/pool_op_rtc_gpu.cc.o
[ 69%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/db/create_db_op_gpu.cc.o
[ 69%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/distributed/file_store_handler_op_gpu.cc.o
[ 70%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/conv_op_cache_cudnn.cc.o
[ 70%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/conv_op_cudnn.cc.o
[ 70%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/conv_transpose_op_cudnn.cc.o
[ 70%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/dropout_op_cudnn.cc.o
[ 70%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/local_response_normalization_op_cudnn.cc.o
[ 71%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/recurrent_op_cudnn.cc.o
[ 71%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/relu_op_cudnn.cc.o
[ 71%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/softmax_op_cudnn.cc.o
[ 71%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/spatial_batch_norm_op_cudnn.cc.o
[ 71%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/transpose_op_cudnn.cc.o
[ 71%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/communicator_op_gpu.cc.o
[ 72%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/concat_split_op_gpu.cc.o
[ 72%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/conv_op_gpu.cc.o
[ 72%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/conv_op_shared_gpu.cc.o
[ 72%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/conv_transpose_op_gpu.cc.o
[ 72%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/counter_ops_gpu.cc.o
[ 72%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/free_op_gpu.cc.o
[ 73%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/fully_connected_op_gpu.cc.o
[ 73%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/im2col_op_gpu.cc.o
[ 73%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/load_save_op_gpu.cc.o
[ 73%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/matmul_op_gpu.cc.o
[ 73%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/pack_segments_op_gpu.cc.o
[ 73%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/prepend_dim_op_gpu.cc.o
[ 74%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/recurrent_network_blob_fetcher_op_gpu.cc.o
[ 74%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/recurrent_network_executor_gpu.cc.o
[ 74%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/recurrent_network_op_gpu.cc.o
[ 74%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/reshape_op_gpu.cc.o
[ 74%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/scale_op_gpu.cc.o
[ 75%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/shape_op_gpu.cc.o
[ 75%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/stop_gradient_gpu.cc.o
[ 75%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/tensor_protos_db_input_gpu.cc.o
[ 75%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/utility_ops_gpu.cc.o
[ 75%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/operators/zero_gradient_op_gpu.cc.o
[ 75%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/queue/queue_ops_gpu.cc.o
[ 76%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/sgd/iter_op_gpu.cc.o
[ 76%] Building CXX object caffe2/CMakeFiles/Caffe2_GPU.dir/sgd/learning_rate_op_gpu.cc.o
[ 76%] Linking CXX shared library libCaffe2_GPU.so
[ 76%] Built target Caffe2_GPU
Scanning dependencies of target cpuid_test
Scanning dependencies of target typeid_test
Scanning dependencies of target caffe2_pybind11_state
Scanning dependencies of target operator_test
Scanning dependencies of target timer_test
Scanning dependencies of target conv_transpose_op_mobile_test
Scanning dependencies of target caffe2_pybind11_state_gpu
Scanning dependencies of target fatal_signal_asan_no_sig_test
[ 76%] Building CXX object caffe2/CMakeFiles/cpuid_test.dir/utils/cpuid_test.cc.o
[ 76%] Building CXX object caffe2/CMakeFiles/timer_test.dir/core/timer_test.cc.o
[ 76%] Building CXX object caffe2/CMakeFiles/fatal_signal_asan_no_sig_test.dir/utils/fatal_signal_asan_no_sig_test.cc.o
[ 76%] Building CXX object caffe2/CMakeFiles/typeid_test.dir/core/typeid_test.cc.o
[ 76%] Building CXX object caffe2/CMakeFiles/conv_transpose_op_mobile_test.dir/operators/conv_transpose_op_mobile_test.cc.o
[ 76%] Building CXX object caffe2/CMakeFiles/operator_test.dir/core/operator_test.cc.o
[ 77%] Building CXX object caffe2/CMakeFiles/caffe2_pybind11_state.dir/python/pybind_state.cc.o
[ 77%] Building CXX object caffe2/CMakeFiles/caffe2_pybind11_state_gpu.dir/python/pybind_state.cc.o
[ 77%] Linking CXX executable binaries/cpuid_test
[ 77%] Built target cpuid_test
Scanning dependencies of target conv_to_nnpack_transform_test
[ 77%] Linking CXX executable binaries/timer_test
[ 78%] Building CXX object caffe2/CMakeFiles/conv_to_nnpack_transform_test.dir/transforms/conv_to_nnpack_transform_test.cc.o
[ 78%] Built target timer_test
Scanning dependencies of target smart_tensor_printer_test
[ 78%] Building CXX object caffe2/CMakeFiles/smart_tensor_printer_test.dir/utils/smart_tensor_printer_test.cc.o
[ 78%] Linking CXX executable binaries/fatal_signal_asan_no_sig_test
[ 78%] Built target fatal_signal_asan_no_sig_test
Scanning dependencies of target registry_test
[ 78%] Building CXX object caffe2/CMakeFiles/registry_test.dir/core/registry_test.cc.o
[ 78%] Linking CXX executable binaries/typeid_test
[ 78%] Built target typeid_test
Scanning dependencies of target workspace_test
[ 78%] Building CXX object caffe2/CMakeFiles/workspace_test.dir/core/workspace_test.cc.o
[ 78%] Linking CXX executable binaries/registry_test
[ 78%] Linking CXX executable binaries/conv_transpose_op_mobile_test
[ 78%] Built target registry_test
[ 78%] Building CXX object caffe2/CMakeFiles/caffe2_pybind11_state_gpu.dir/python/pybind_state_mkl.cc.o
[ 78%] Built target conv_transpose_op_mobile_test
[ 78%] Building CXX object caffe2/CMakeFiles/caffe2_pybind11_state_gpu.dir/python/pybind_state_gpu.cc.o
[ 78%] Linking CXX executable binaries/smart_tensor_printer_test
[ 78%] Built target smart_tensor_printer_test
Scanning dependencies of target context_gpu_test
[ 78%] Building CXX object caffe2/CMakeFiles/context_gpu_test.dir/core/context_gpu_test.cc.o
[ 78%] Linking CXX executable binaries/conv_to_nnpack_transform_test
[ 78%] Built target conv_to_nnpack_transform_test
Scanning dependencies of target operator_fallback_gpu_test
[ 78%] Building CXX object caffe2/CMakeFiles/operator_fallback_gpu_test.dir/operators/operator_fallback_gpu_test.cc.o
[ 78%] Linking CXX executable binaries/operator_test
Scanning dependencies of target blob_test
[ 78%] Building CXX object caffe2/CMakeFiles/blob_test.dir/core/blob_test.cc.o
[ 79%] Linking CXX executable binaries/workspace_test
[ 79%] Built target operator_test
[ 79%] Building CXX object caffe2/CMakeFiles/caffe2_pybind11_state.dir/python/pybind_state_mkl.cc.o
[ 79%] Built target workspace_test
Scanning dependencies of target parallel_net_test
[ 79%] Building CXX object caffe2/CMakeFiles/parallel_net_test.dir/core/parallel_net_test.cc.o
[ 80%] Linking CXX executable binaries/context_gpu_test
[ 80%] Built target context_gpu_test
Scanning dependencies of target fixed_divisor_test
[ 80%] Building CXX object caffe2/CMakeFiles/fixed_divisor_test.dir/utils/fixed_divisor_test.cc.o
[ 80%] Linking CXX executable binaries/fixed_divisor_test
Scanning dependencies of target init_test
[ 80%] Built target fixed_divisor_test
Scanning dependencies of target transform_test
[ 80%] Building CXX object caffe2/CMakeFiles/init_test.dir/core/init_test.cc.o
[ 80%] Linking CXX executable binaries/operator_fallback_gpu_test
[ 81%] Building CXX object caffe2/CMakeFiles/transform_test.dir/core/transform_test.cc.o
[ 81%] Built target operator_fallback_gpu_test
Scanning dependencies of target event_test
[ 81%] Building CXX object caffe2/CMakeFiles/event_test.dir/core/event_test.cc.o
Scanning dependencies of target graph_test
[ 81%] Building CXX object caffe2/CMakeFiles/graph_test.dir/core/graph_test.cc.o
[ 81%] Linking CXX executable binaries/init_test
[ 81%] Built target init_test
Scanning dependencies of target string_ops_test
[ 82%] Building CXX object caffe2/CMakeFiles/string_ops_test.dir/operators/string_ops_test.cc.o
[ 82%] Linking CXX executable binaries/parallel_net_test
[ 82%] Built target parallel_net_test
Scanning dependencies of target predictor_test
[ 82%] Building CXX object caffe2/CMakeFiles/predictor_test.dir/core/predictor_test.cc.o
[ 82%] Linking CXX executable binaries/event_test
[ 82%] Built target event_test
Scanning dependencies of target observer_test
[ 82%] Building CXX object caffe2/CMakeFiles/observer_test.dir/core/observer_test.cc.o
[ 82%] Linking CXX executable binaries/graph_test
[ 82%] Built target graph_test
Scanning dependencies of target logging_test
[ 83%] Building CXX object caffe2/CMakeFiles/logging_test.dir/core/logging_test.cc.o
[ 83%] Linking CXX executable binaries/transform_test
[ 83%] Linking CXX executable binaries/string_ops_test
[ 83%] Linking CXX executable binaries/predictor_test
[ 83%] Built target transform_test
Scanning dependencies of target net_test
[ 83%] Building CXX object caffe2/CMakeFiles/net_test.dir/core/net_test.cc.o
[ 83%] Built target string_ops_test
Scanning dependencies of target elementwise_op_test
[ 83%] Built target predictor_test
Scanning dependencies of target boolean_unmask_ops_test
[ 83%] Building CXX object caffe2/CMakeFiles/elementwise_op_test.dir/operators/elementwise_op_test.cc.o
[ 83%] Building CXX object caffe2/CMakeFiles/boolean_unmask_ops_test.dir/operators/boolean_unmask_ops_test.cc.o
[ 83%] Linking CXX executable binaries/observer_test
[ 83%] Linking CXX executable binaries/logging_test
[ 83%] Built target observer_test
Scanning dependencies of target conv_op_cache_cudnn_test
[ 83%] Building CXX object caffe2/CMakeFiles/conv_op_cache_cudnn_test.dir/operators/conv_op_cache_cudnn_test.cc.o
[ 83%] Built target logging_test
Scanning dependencies of target reshape_op_gpu_test
[ 83%] Building CXX object caffe2/CMakeFiles/reshape_op_gpu_test.dir/operators/reshape_op_gpu_test.cc.o
[ 84%] Linking CXX shared module python/caffe2_pybind11_state_gpu.so
[ 84%] Linking CXX shared module python/caffe2_pybind11_state.so
[ 84%] Built target caffe2_pybind11_state_gpu
Scanning dependencies of target operator_schema_test
[ 84%] Building CXX object caffe2/CMakeFiles/operator_schema_test.dir/core/operator_schema_test.cc.o
[ 84%] Built target caffe2_pybind11_state
Scanning dependencies of target fully_connected_op_test
[ 84%] Building CXX object caffe2/CMakeFiles/fully_connected_op_test.dir/operators/fully_connected_op_test.cc.o
[ 84%] Linking CXX executable binaries/boolean_unmask_ops_test
[ 84%] Linking CXX executable binaries/conv_op_cache_cudnn_test
[ 84%] Built target boolean_unmask_ops_test
Scanning dependencies of target simple_queue_test
[ 84%] Linking CXX executable binaries/elementwise_op_test
[ 84%] Building CXX object caffe2/CMakeFiles/simple_queue_test.dir/utils/simple_queue_test.cc.o
[ 84%] Built target elementwise_op_test
[ 84%] Built target conv_op_cache_cudnn_test
Scanning dependencies of target text_file_reader_utils_test
Scanning dependencies of target math_gpu_test
[ 84%] Building CXX object caffe2/CMakeFiles/text_file_reader_utils_test.dir/operators/text_file_reader_utils_test.cc.o
[ 84%] Building CXX object caffe2/CMakeFiles/math_gpu_test.dir/utils/math_gpu_test.cc.o
[ 85%] Linking CXX executable binaries/net_test
[ 85%] Built target net_test
Scanning dependencies of target stats_test
[ 85%] Building CXX object caffe2/CMakeFiles/stats_test.dir/core/stats_test.cc.o
[ 85%] Linking CXX executable binaries/reshape_op_gpu_test
[ 85%] Built target reshape_op_gpu_test
Scanning dependencies of target event_gpu_test
[ 86%] Linking CXX executable binaries/simple_queue_test
[ 86%] Building CXX object caffe2/CMakeFiles/event_gpu_test.dir/core/event_gpu_test.cc.o
[ 86%] Built target simple_queue_test
Scanning dependencies of target utility_ops_test
[ 86%] Building CXX object caffe2/CMakeFiles/utility_ops_test.dir/operators/utility_ops_test.cc.o
[ 86%] Linking CXX executable binaries/fully_connected_op_test
[ 86%] Built target fully_connected_op_test
Scanning dependencies of target utility_ops_gpu_test
[ 87%] Building CXX object caffe2/CMakeFiles/utility_ops_gpu_test.dir/operators/utility_ops_gpu_test.cc.o
[ 87%] Linking CXX executable binaries/stats_test
[ 87%] Built target stats_test
Scanning dependencies of target context_test
[ 87%] Linking CXX executable binaries/text_file_reader_utils_test
[ 87%] Linking CXX executable binaries/operator_schema_test
[ 87%] Building CXX object caffe2/CMakeFiles/context_test.dir/core/context_test.cc.o
[ 87%] Built target operator_schema_test
CMakeFiles/text_file_reader_utils_test.dir/operators/text_file_reader_utils_test.cc.o: In function `caffe2::TextFileReaderUtilsTest_TokenizeTest_Test::TestBody()':
text_file_reader_utils_test.cc:(.text+0x1a02): warning: the use of `tmpnam' is dangerous, better use `mkstemp'
Scanning dependencies of target common_subexpression_elimination_test
[ 87%] Built target text_file_reader_utils_test
Scanning dependencies of target proto_utils_test
[ 87%] Building CXX object caffe2/CMakeFiles/proto_utils_test.dir/utils/proto_utils_test.cc.o
[ 87%] Building CXX object caffe2/CMakeFiles/common_subexpression_elimination_test.dir/transforms/common_subexpression_elimination_test.cc.o
[ 88%] Linking CXX executable binaries/event_gpu_test
[ 88%] Built target event_gpu_test
Scanning dependencies of target pattern_net_transform_test
[ 89%] Building CXX object caffe2/CMakeFiles/pattern_net_transform_test.dir/transforms/pattern_net_transform_test.cc.o
[ 89%] Linking CXX executable binaries/math_gpu_test
[ 89%] Built target math_gpu_test
Scanning dependencies of target math_test
[ 89%] Linking CXX executable binaries/blob_test
[ 90%] Linking CXX executable binaries/proto_utils_test
[ 90%] Building CXX object caffe2/CMakeFiles/math_test.dir/utils/math_test.cc.o
CMakeFiles/proto_utils_test.dir/utils/proto_utils_test.cc.o: In function `caffe2::ProtoUtilsTest_SimpleReadWrite_Test::TestBody()':
proto_utils_test.cc:(.text+0x31): warning: the use of `tmpnam' is dangerous, better use `mkstemp'
[ 90%] Built target proto_utils_test
Scanning dependencies of target blob_gpu_test
CMakeFiles/blob_test.dir/core/blob_test.cc.o: In function `caffe2::(anonymous namespace)::TypedTensorTest_BigTensorSerialization_Test<float>::TestBody()':
blob_test.cc:(.text+0x3e3c1): warning: the use of `tmpnam' is dangerous, better use `mkstemp'
[ 90%] Built target blob_test
Scanning dependencies of target operator_gpu_test
[ 91%] Building CXX object caffe2/CMakeFiles/blob_gpu_test.dir/core/blob_gpu_test.cc.o
[ 92%] Building CXX object caffe2/CMakeFiles/operator_gpu_test.dir/core/operator_gpu_test.cc.o
[ 92%] Linking CXX executable binaries/utility_ops_test
[ 92%] Linking CXX executable binaries/context_test
[ 92%] Built target utility_ops_test
Scanning dependencies of target elementwise_op_gpu_test
[ 92%] Built target context_test
Scanning dependencies of target fully_connected_op_gpu_test
[ 93%] Building CXX object caffe2/CMakeFiles/elementwise_op_gpu_test.dir/operators/elementwise_op_gpu_test.cc.o
[ 93%] Building CXX object caffe2/CMakeFiles/fully_connected_op_gpu_test.dir/operators/fully_connected_op_gpu_test.cc.o
[ 93%] Linking CXX executable binaries/utility_ops_gpu_test
[ 93%] Built target utility_ops_gpu_test
Scanning dependencies of target tutorial_blob
[ 93%] Building CXX object caffe2/binaries/CMakeFiles/tutorial_blob.dir/tutorial_blob.cc.o
[ 93%] Linking CXX executable binaries/common_subexpression_elimination_test
[ 93%] Built target common_subexpression_elimination_test
Scanning dependencies of target print_core_object_sizes
[ 94%] Building CXX object caffe2/binaries/CMakeFiles/print_core_object_sizes.dir/print_core_object_sizes.cc.o
[ 95%] Linking CXX executable binaries/math_test
[ 95%] Built target math_test
Scanning dependencies of target inspect_gpus
[ 95%] Building CXX object caffe2/binaries/CMakeFiles/inspect_gpus.dir/inspect_gpus.cc.o
[ 95%] Linking CXX executable binaries/tutorial_blob
[ 95%] Built target tutorial_blob
Scanning dependencies of target predictor_verifier
[ 95%] Linking CXX executable binaries/operator_gpu_test
[ 95%] Building CXX object caffe2/binaries/CMakeFiles/predictor_verifier.dir/predictor_verifier.cc.o
[ 95%] Linking CXX executable binaries/inspect_gpus
[ 95%] Built target operator_gpu_test
Scanning dependencies of target convert_db
[ 96%] Building CXX object caffe2/binaries/CMakeFiles/convert_db.dir/convert_db.cc.o
[ 96%] Built target inspect_gpus
Scanning dependencies of target print_registered_core_operators
[ 96%] Building CXX object caffe2/binaries/CMakeFiles/print_registered_core_operators.dir/print_registered_core_operators.cc.o
[ 97%] Linking CXX executable binaries/fully_connected_op_gpu_test
[ 97%] Linking CXX executable binaries/print_core_object_sizes
[ 97%] Built target fully_connected_op_gpu_test
Scanning dependencies of target convert_caffe_image_db
[ 97%] Building CXX object caffe2/binaries/CMakeFiles/convert_caffe_image_db.dir/convert_caffe_image_db.cc.o
[ 97%] Built target print_core_object_sizes
[ 97%] Linking CXX executable binaries/elementwise_op_gpu_test
Scanning dependencies of target db_throughput
[ 97%] Linking CXX executable binaries/pattern_net_transform_test
[ 98%] Building CXX object caffe2/binaries/CMakeFiles/db_throughput.dir/db_throughput.cc.o
[ 98%] Built target elementwise_op_gpu_test
Scanning dependencies of target run_plan
[ 98%] Building CXX object caffe2/binaries/CMakeFiles/run_plan.dir/run_plan.cc.o
[ 98%] Built target pattern_net_transform_test
Scanning dependencies of target make_mnist_db
[ 98%] Building CXX object caffe2/binaries/CMakeFiles/make_mnist_db.dir/make_mnist_db.cc.o
[ 98%] Linking CXX executable binaries/predictor_verifier
[ 98%] Built target predictor_verifier
Scanning dependencies of target speed_benchmark
[ 98%] Linking CXX executable binaries/convert_db
[ 98%] Building CXX object caffe2/binaries/CMakeFiles/speed_benchmark.dir/speed_benchmark.cc.o
[ 98%] Built target convert_db
Scanning dependencies of target make_cifar_db
[ 98%] Building CXX object caffe2/binaries/CMakeFiles/make_cifar_db.dir/make_cifar_db.cc.o
[ 98%] Linking CXX executable binaries/print_registered_core_operators
[ 98%] Built target print_registered_core_operators
[ 98%] Linking CXX executable binaries/blob_gpu_test
Scanning dependencies of target split_db
[ 98%] Building CXX object caffe2/binaries/CMakeFiles/split_db.dir/split_db.cc.o
[ 98%] Built target blob_gpu_test
[ 98%] Linking CXX executable binaries/run_plan
[ 98%] Linking CXX executable binaries/db_throughput
[ 99%] Linking CXX executable binaries/make_mnist_db
[ 99%] Built target run_plan
[ 99%] Built target db_throughput
[ 99%] Linking CXX executable binaries/convert_caffe_image_db
[ 99%] Built target make_mnist_db
[ 99%] Built target convert_caffe_image_db
[ 99%] Linking CXX executable binaries/make_cifar_db
[ 99%] Built target make_cifar_db
[100%] Linking CXX executable binaries/speed_benchmark
[100%] Linking CXX executable binaries/split_db
[100%] Built target split_db
[100%] Built target speed_benchmark
Install the project...
-- Install configuration: "Release"
-- Installing: /usr/local/lib/libgmock.so
-- Installing: /usr/local/lib/libgmock_main.so
-- Installing: /usr/local/include/gmock
-- Installing: /usr/local/include/gmock/gmock-actions.h
-- Installing: /usr/local/include/gmock/gmock-cardinalities.h
-- Installing: /usr/local/include/gmock/gmock-generated-actions.h
-- Installing: /usr/local/include/gmock/gmock-generated-actions.h.pump
-- Installing: /usr/local/include/gmock/gmock-generated-function-mockers.h
-- Installing: /usr/local/include/gmock/gmock-generated-function-mockers.h.pump
-- Installing: /usr/local/include/gmock/gmock-generated-matchers.h
-- Installing: /usr/local/include/gmock/gmock-generated-matchers.h.pump
-- Installing: /usr/local/include/gmock/gmock-generated-nice-strict.h
-- Installing: /usr/local/include/gmock/gmock-generated-nice-strict.h.pump
-- Installing: /usr/local/include/gmock/gmock-matchers.h
-- Installing: /usr/local/include/gmock/gmock-more-actions.h
-- Installing: /usr/local/include/gmock/gmock-more-matchers.h
-- Installing: /usr/local/include/gmock/gmock-spec-builders.h
-- Installing: /usr/local/include/gmock/gmock.h
-- Installing: /usr/local/include/gmock/internal
-- Installing: /usr/local/include/gmock/internal/custom
-- Installing: /usr/local/include/gmock/internal/custom/gmock-generated-actions.h
-- Installing: /usr/local/include/gmock/internal/custom/gmock-generated-actions.h.pump
-- Installing: /usr/local/include/gmock/internal/custom/gmock-matchers.h
-- Installing: /usr/local/include/gmock/internal/custom/gmock-port.h
-- Installing: /usr/local/include/gmock/internal/gmock-generated-internal-utils.h
-- Installing: /usr/local/include/gmock/internal/gmock-generated-internal-utils.h.pump
-- Installing: /usr/local/include/gmock/internal/gmock-internal-utils.h
-- Installing: /usr/local/include/gmock/internal/gmock-port.h
-- Installing: /usr/local/lib/libgtest.so
-- Set runtime path of "/usr/local/lib/libgtest.so" to ""
-- Installing: /usr/local/lib/libgtest_main.so
-- Set runtime path of "/usr/local/lib/libgtest_main.so" to ""
-- Installing: /usr/local/include/gtest
-- Installing: /usr/local/include/gtest/gtest-death-test.h
-- Installing: /usr/local/include/gtest/gtest-message.h
-- Installing: /usr/local/include/gtest/gtest-param-test.h
-- Installing: /usr/local/include/gtest/gtest-param-test.h.pump
-- Installing: /usr/local/include/gtest/gtest-printers.h
-- Installing: /usr/local/include/gtest/gtest-spi.h
-- Installing: /usr/local/include/gtest/gtest-test-part.h
-- Installing: /usr/local/include/gtest/gtest-typed-test.h
-- Installing: /usr/local/include/gtest/gtest.h
-- Installing: /usr/local/include/gtest/gtest_pred_impl.h
-- Installing: /usr/local/include/gtest/gtest_prod.h
-- Installing: /usr/local/include/gtest/internal
-- Installing: /usr/local/include/gtest/internal/custom
-- Installing: /usr/local/include/gtest/internal/custom/gtest-port.h
-- Installing: /usr/local/include/gtest/internal/custom/gtest-printers.h
-- Installing: /usr/local/include/gtest/internal/custom/gtest.h
-- Installing: /usr/local/include/gtest/internal/gtest-death-test-internal.h
-- Installing: /usr/local/include/gtest/internal/gtest-filepath.h
-- Installing: /usr/local/include/gtest/internal/gtest-internal.h
-- Installing: /usr/local/include/gtest/internal/gtest-linked_ptr.h
-- Installing: /usr/local/include/gtest/internal/gtest-param-util-generated.h
-- Installing: /usr/local/include/gtest/internal/gtest-param-util-generated.h.pump
-- Installing: /usr/local/include/gtest/internal/gtest-param-util.h
-- Installing: /usr/local/include/gtest/internal/gtest-port-arch.h
-- Installing: /usr/local/include/gtest/internal/gtest-port.h
-- Installing: /usr/local/include/gtest/internal/gtest-string.h
-- Installing: /usr/local/include/gtest/internal/gtest-tuple.h
-- Installing: /usr/local/include/gtest/internal/gtest-tuple.h.pump
-- Installing: /usr/local/include/gtest/internal/gtest-type-util.h
-- Installing: /usr/local/include/gtest/internal/gtest-type-util.h.pump
-- Installing: /usr/local/lib/libbenchmark.so.0.0.0
-- Installing: /usr/local/lib/libbenchmark.so.0
-- Installing: /usr/local/lib/libbenchmark.so
-- Installing: /usr/local/include/benchmark
-- Installing: /usr/local/include/benchmark/benchmark.h
-- Installing: /usr/local/include/benchmark/benchmark_api.h
-- Installing: /usr/local/include/benchmark/macros.h
-- Installing: /usr/local/include/benchmark/reporter.h
-- Installing: /usr/local/include/caffe/proto/caffe.pb.h
-- Installing: /usr/local/lib/libCaffe2_CPU.so
-- Set runtime path of "/usr/local/lib/libCaffe2_CPU.so" to ""
-- Installing: /usr/local/include/caffe2
-- Installing: /usr/local/include/caffe2/binaries
-- Installing: /usr/local/include/caffe2/contrib
-- Installing: /usr/local/include/caffe2/contrib/docker-ubuntu-14.04
-- Installing: /usr/local/include/caffe2/contrib/gloo
-- Installing: /usr/local/include/caffe2/contrib/gloo/allreduce_ops.h
-- Installing: /usr/local/include/caffe2/contrib/gloo/barrier_ops.h
-- Installing: /usr/local/include/caffe2/contrib/gloo/broadcast_ops.h
-- Installing: /usr/local/include/caffe2/contrib/gloo/common.h
-- Installing: /usr/local/include/caffe2/contrib/gloo/common_world_ops.h
-- Installing: /usr/local/include/caffe2/contrib/gloo/context.h
-- Installing: /usr/local/include/caffe2/contrib/gloo/store_handler.h
-- Installing: /usr/local/include/caffe2/contrib/libopencl-stub
-- Installing: /usr/local/include/caffe2/contrib/nccl
-- Installing: /usr/local/include/caffe2/contrib/nccl/cuda_nccl_gpu.h
-- Installing: /usr/local/include/caffe2/contrib/nervana
-- Installing: /usr/local/include/caffe2/contrib/nervana/nervana.h
-- Installing: /usr/local/include/caffe2/contrib/nervana/nervana_c_api.h
-- Installing: /usr/local/include/caffe2/contrib/nnpack
-- Installing: /usr/local/include/caffe2/contrib/observers
-- Installing: /usr/local/include/caffe2/contrib/observers/time_observer.h
-- Installing: /usr/local/include/caffe2/contrib/prof
-- Installing: /usr/local/include/caffe2/contrib/prof/htrace_conf.h
-- Installing: /usr/local/include/caffe2/contrib/prof/prof_dag_net.h
-- Installing: /usr/local/include/caffe2/contrib/prof/prof_dag_stats_op.h
-- Installing: /usr/local/include/caffe2/contrib/shm_mutex
-- Installing: /usr/local/include/caffe2/contrib/shm_mutex/shm_mutex.h
-- Installing: /usr/local/include/caffe2/contrib/torch
-- Installing: /usr/local/include/caffe2/contrib/torch/torch_op.h
-- Installing: /usr/local/include/caffe2/contrib/warpctc
-- Installing: /usr/local/include/caffe2/contrib/warpctc/ctc_op.h
-- Installing: /usr/local/include/caffe2/core
-- Installing: /usr/local/include/caffe2/core/allocator.h
-- Installing: /usr/local/include/caffe2/core/asan.h
-- Installing: /usr/local/include/caffe2/core/blob.h
-- Installing: /usr/local/include/caffe2/core/blob_serialization.h
-- Installing: /usr/local/include/caffe2/core/blob_serializer_base.h
-- Installing: /usr/local/include/caffe2/core/blob_stats.h
-- Installing: /usr/local/include/caffe2/core/common.h
-- Installing: /usr/local/include/caffe2/core/common_cudnn.h
-- Installing: /usr/local/include/caffe2/core/common_gpu.h
-- Installing: /usr/local/include/caffe2/core/common_omp.h
-- Installing: /usr/local/include/caffe2/core/context.h
-- Installing: /usr/local/include/caffe2/core/context_gpu.h
-- Installing: /usr/local/include/caffe2/core/db.h
-- Installing: /usr/local/include/caffe2/core/event.h
-- Installing: /usr/local/include/caffe2/core/flags.h
-- Installing: /usr/local/include/caffe2/core/graph.h
-- Installing: /usr/local/include/caffe2/core/init.h
-- Installing: /usr/local/include/caffe2/core/logging.h
-- Installing: /usr/local/include/caffe2/core/logging_is_google_glog.h
-- Installing: /usr/local/include/caffe2/core/logging_is_not_google_glog.h
-- Installing: /usr/local/include/caffe2/core/macros.h
-- Installing: /usr/local/include/caffe2/core/memonger.h
-- Installing: /usr/local/include/caffe2/core/net.h
-- Installing: /usr/local/include/caffe2/core/net_async_dag_gpu.h
-- Installing: /usr/local/include/caffe2/core/net_dag.h
-- Installing: /usr/local/include/caffe2/core/net_simple.h
-- Installing: /usr/local/include/caffe2/core/observer.h
-- Installing: /usr/local/include/caffe2/core/operator.h
-- Installing: /usr/local/include/caffe2/core/operator_gradient.h
-- Installing: /usr/local/include/caffe2/core/operator_schema.h
-- Installing: /usr/local/include/caffe2/core/plan_executor.h
-- Installing: /usr/local/include/caffe2/core/predictor.h
-- Installing: /usr/local/include/caffe2/core/qtensor.h
-- Installing: /usr/local/include/caffe2/core/qtensor_serialization.h
-- Installing: /usr/local/include/caffe2/core/registry.h
-- Installing: /usr/local/include/caffe2/core/scope_guard.h
-- Installing: /usr/local/include/caffe2/core/static_tracepoint.h
-- Installing: /usr/local/include/caffe2/core/static_tracepoint_elfx86.h
-- Installing: /usr/local/include/caffe2/core/stats.h
-- Installing: /usr/local/include/caffe2/core/tensor.h
-- Installing: /usr/local/include/caffe2/core/timer.h
-- Installing: /usr/local/include/caffe2/core/transform.h
-- Installing: /usr/local/include/caffe2/core/typeid.h
-- Installing: /usr/local/include/caffe2/core/types.h
-- Installing: /usr/local/include/caffe2/core/workspace.h
-- Installing: /usr/local/include/caffe2/cuda_rtc
-- Installing: /usr/local/include/caffe2/cuda_rtc/common_rtc.h
-- Installing: /usr/local/include/caffe2/db
-- Installing: /usr/local/include/caffe2/db/create_db_op.h
-- Installing: /usr/local/include/caffe2/distributed
-- Installing: /usr/local/include/caffe2/distributed/file_store_handler.h
-- Installing: /usr/local/include/caffe2/distributed/file_store_handler_op.h
-- Installing: /usr/local/include/caffe2/distributed/redis_store_handler.h
-- Installing: /usr/local/include/caffe2/distributed/redis_store_handler_op.h
-- Installing: /usr/local/include/caffe2/distributed/store_handler.h
-- Installing: /usr/local/include/caffe2/distributed/store_ops.h
-- Installing: /usr/local/include/caffe2/experiments
-- Installing: /usr/local/include/caffe2/experiments/operators
-- Installing: /usr/local/include/caffe2/experiments/operators/fully_connected_op_decomposition.h
-- Installing: /usr/local/include/caffe2/experiments/operators/fully_connected_op_prune.h
-- Installing: /usr/local/include/caffe2/experiments/operators/fully_connected_op_sparse.h
-- Installing: /usr/local/include/caffe2/experiments/operators/funhash_op.h
-- Installing: /usr/local/include/caffe2/experiments/operators/sparse_funhash_op.h
-- Installing: /usr/local/include/caffe2/experiments/operators/sparse_matrix_reshape_op.h
-- Installing: /usr/local/include/caffe2/experiments/operators/tt_contraction_op.h
-- Installing: /usr/local/include/caffe2/experiments/operators/tt_pad_op.h
-- Installing: /usr/local/include/caffe2/experiments/python
-- Installing: /usr/local/include/caffe2/image
-- Installing: /usr/local/include/caffe2/image/image_input_op.h
-- Installing: /usr/local/include/caffe2/image/transform_gpu.h
-- Installing: /usr/local/include/caffe2/mkl
-- Installing: /usr/local/include/caffe2/mkl/mkl_utils.h
-- Installing: /usr/local/include/caffe2/mkl/operators
-- Installing: /usr/local/include/caffe2/mkl/operators/operator_fallback_mkl.h
-- Installing: /usr/local/include/caffe2/mkl/utils
-- Installing: /usr/local/include/caffe2/mkl/utils/mkl_context.h
-- Installing: /usr/local/include/caffe2/mkl/utils/mkl_dnn_cppwrapper.h
-- Installing: /usr/local/include/caffe2/mkl/utils/mkl_memory.h
-- Installing: /usr/local/include/caffe2/mkl/utils/mkl_operator.h
-- Installing: /usr/local/include/caffe2/mkl/utils/mkl_version_check.h
-- Installing: /usr/local/include/caffe2/mkl/utils/sgemm_pack.h
-- Installing: /usr/local/include/caffe2/mobile
-- Installing: /usr/local/include/caffe2/mobile/contrib
-- Installing: /usr/local/include/caffe2/mobile/contrib/ios
-- Installing: /usr/local/include/caffe2/mobile/contrib/ios/ios_caffe.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/ios/ios_caffe_defines.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/ios/ios_caffe_predictor.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/ios/mpscnn
-- Installing: /usr/local/include/caffe2/mobile/contrib/ios/mpscnn/mpscnn.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/ios/mpscnn/mpscnn_context.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/ios/mpscnn/mpscnn_graph_mask.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/ios/mpscnn/mpscnn_kernels.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/ios/mpscnn/mpscnn_test.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/libopencl-stub
-- Installing: /usr/local/include/caffe2/mobile/contrib/libopencl-stub/include
-- Installing: /usr/local/include/caffe2/mobile/contrib/libopencl-stub/include/CL
-- Installing: /usr/local/include/caffe2/mobile/contrib/libopencl-stub/include/CL/cl.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/libopencl-stub/include/CL/cl_ext.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/libopencl-stub/include/CL/cl_gl.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/libopencl-stub/include/CL/cl_gl_ext.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/libopencl-stub/include/CL/cl_platform.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/libopencl-stub/include/CL/opencl.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/libopencl-stub/include/libopencl.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/libopencl-stub/src
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/android
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/android/AndroidGLContext.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/android/arm_neon_support.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/android/gl3stub.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/DataTransfer.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/GL.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/GLContext.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/GLFilter.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/GLImage.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/GLImageAllocator.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/GLLogging.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/GLPBO.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/GLPlainTexture.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/GLPredictor.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/GLTexture.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/ImageAllocator.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/arm_neon_support.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/core/rewrite_net.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/ios
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/ios/IOSGLContext.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/ios/IOSGLImageAllocator.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/ios/IOSGLTexture.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/operators
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/test
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/test/TestGLConvolution.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/opengl/test/opengl_test.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/snpe
-- Installing: /usr/local/include/caffe2/mobile/contrib/snpe/snpe_ffi.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/ulp2
-- Installing: /usr/local/include/caffe2/mobile/contrib/ulp2/ulp.h
-- Installing: /usr/local/include/caffe2/mobile/contrib/ulp2/ulp_neon.h
-- Installing: /usr/local/include/caffe2/mpi
-- Installing: /usr/local/include/caffe2/mpi/mpi_common.h
-- Installing: /usr/local/include/caffe2/mpi/mpi_ops.h
-- Installing: /usr/local/include/caffe2/operators
-- Installing: /usr/local/include/caffe2/operators/accumulate_op.h
-- Installing: /usr/local/include/caffe2/operators/accuracy_op.h
-- Installing: /usr/local/include/caffe2/operators/apmeter_op.h
-- Installing: /usr/local/include/caffe2/operators/batch_box_cox_op.h
-- Installing: /usr/local/include/caffe2/operators/batch_gather_ops.h
-- Installing: /usr/local/include/caffe2/operators/batch_matmul_op.h
-- Installing: /usr/local/include/caffe2/operators/boolean_mask_ops.h
-- Installing: /usr/local/include/caffe2/operators/boolean_unmask_ops.h
-- Installing: /usr/local/include/caffe2/operators/cast_op.h
-- Installing: /usr/local/include/caffe2/operators/channel_shuffle_op.h
-- Installing: /usr/local/include/caffe2/operators/clip_op.h
-- Installing: /usr/local/include/caffe2/operators/concat_split_op.h
-- Installing: /usr/local/include/caffe2/operators/conditional_op.h
-- Installing: /usr/local/include/caffe2/operators/conv_op.h
-- Installing: /usr/local/include/caffe2/operators/conv_op_cache_cudnn.h
-- Installing: /usr/local/include/caffe2/operators/conv_op_impl.h
-- Installing: /usr/local/include/caffe2/operators/conv_op_shared.h
-- Installing: /usr/local/include/caffe2/operators/conv_pool_op_base.h
-- Installing: /usr/local/include/caffe2/operators/conv_transpose_op.h
-- Installing: /usr/local/include/caffe2/operators/conv_transpose_op_impl.h
-- Installing: /usr/local/include/caffe2/operators/conv_transpose_op_mobile.h
-- Installing: /usr/local/include/caffe2/operators/conv_transpose_op_mobile_impl.h
-- Installing: /usr/local/include/caffe2/operators/conv_transpose_unpool_op_base.h
-- Installing: /usr/local/include/caffe2/operators/cosine_embedding_criterion_op.h
-- Installing: /usr/local/include/caffe2/operators/counter_ops.h
-- Installing: /usr/local/include/caffe2/operators/cross_entropy_op.h
-- Installing: /usr/local/include/caffe2/operators/dataset_ops.h
-- Installing: /usr/local/include/caffe2/operators/distance_op.h
-- Installing: /usr/local/include/caffe2/operators/do_op.h
-- Installing: /usr/local/include/caffe2/operators/dropout_op.h
-- Installing: /usr/local/include/caffe2/operators/elementwise_linear_op.h
-- Installing: /usr/local/include/caffe2/operators/elementwise_logical_ops.h
-- Installing: /usr/local/include/caffe2/operators/elementwise_op.h
-- Installing: /usr/local/include/caffe2/operators/elementwise_op_test.h
-- Installing: /usr/local/include/caffe2/operators/elu_op.h
-- Installing: /usr/local/include/caffe2/operators/feed_blob_op.h
-- Installing: /usr/local/include/caffe2/operators/filler_op.h
-- Installing: /usr/local/include/caffe2/operators/find_duplicate_elements_op.h
-- Installing: /usr/local/include/caffe2/operators/find_op.h
-- Installing: /usr/local/include/caffe2/operators/free_op.h
-- Installing: /usr/local/include/caffe2/operators/fully_connected_op.h
-- Installing: /usr/local/include/caffe2/operators/given_tensor_fill_op.h
-- Installing: /usr/local/include/caffe2/operators/gru_unit_op.h
-- Installing: /usr/local/include/caffe2/operators/h_softmax_op.h
-- Installing: /usr/local/include/caffe2/operators/half_float_ops.h
-- Installing: /usr/local/include/caffe2/operators/if_op.h
-- Installing: /usr/local/include/caffe2/operators/im2col_op.h
-- Installing: /usr/local/include/caffe2/operators/index_hash_ops.h
-- Installing: /usr/local/include/caffe2/operators/instance_norm_op.h
-- Installing: /usr/local/include/caffe2/operators/layer_norm_op.h
-- Installing: /usr/local/include/caffe2/operators/leaky_relu_op.h
-- Installing: /usr/local/include/caffe2/operators/lengths_reducer_ops.h
-- Installing: /usr/local/include/caffe2/operators/lengths_reducer_rowwise_8bit_ops.h
-- Installing: /usr/local/include/caffe2/operators/lengths_tile_op.h
-- Installing: /usr/local/include/caffe2/operators/lengths_top_k_op.h
-- Installing: /usr/local/include/caffe2/operators/load_save_op.h
-- Installing: /usr/local/include/caffe2/operators/local_response_normalization_op.h
-- Installing: /usr/local/include/caffe2/operators/loss_op.h
-- Installing: /usr/local/include/caffe2/operators/lpnorm_op.h
-- Installing: /usr/local/include/caffe2/operators/lstm_unit_op.h
-- Installing: /usr/local/include/caffe2/operators/map_ops.h
-- Installing: /usr/local/include/caffe2/operators/margin_ranking_criterion_op.h
-- Installing: /usr/local/include/caffe2/operators/math_ops.h
-- Installing: /usr/local/include/caffe2/operators/matmul_op.h
-- Installing: /usr/local/include/caffe2/operators/max_pool_with_index.h
-- Installing: /usr/local/include/caffe2/operators/merge_id_lists_op.h
-- Installing: /usr/local/include/caffe2/operators/multi_class_accuracy_op.h
-- Installing: /usr/local/include/caffe2/operators/no_default_engine_op.h
-- Installing: /usr/local/include/caffe2/operators/normalize_op.h
-- Installing: /usr/local/include/caffe2/operators/one_hot_ops.h
-- Installing: /usr/local/include/caffe2/operators/operator_fallback_gpu.h
-- Installing: /usr/local/include/caffe2/operators/order_switch_ops.h
-- Installing: /usr/local/include/caffe2/operators/pack_rnn_sequence_op.h
-- Installing: /usr/local/include/caffe2/operators/pack_segments.h
-- Installing: /usr/local/include/caffe2/operators/pad_op.h
-- Installing: /usr/local/include/caffe2/operators/partition_ops.h
-- Installing: /usr/local/include/caffe2/operators/perplexity_op.h
-- Installing: /usr/local/include/caffe2/operators/piecewise_linear_transform_op.h
-- Installing: /usr/local/include/caffe2/operators/pool_op.h
-- Installing: /usr/local/include/caffe2/operators/prefetch_op.h
-- Installing: /usr/local/include/caffe2/operators/prelu_op.h
-- Installing: /usr/local/include/caffe2/operators/prepend_dim_op.h
-- Installing: /usr/local/include/caffe2/operators/rank_loss_op.h
-- Installing: /usr/local/include/caffe2/operators/recurrent_network_blob_fetcher_op.h
-- Installing: /usr/local/include/caffe2/operators/recurrent_network_executor.h
-- Installing: /usr/local/include/caffe2/operators/recurrent_network_executor_gpu.h
-- Installing: /usr/local/include/caffe2/operators/recurrent_network_executor_incl.h
-- Installing: /usr/local/include/caffe2/operators/recurrent_network_op.h
-- Installing: /usr/local/include/caffe2/operators/recurrent_op_cudnn.h
-- Installing: /usr/local/include/caffe2/operators/reducer_functors.h
-- Installing: /usr/local/include/caffe2/operators/reduction_ops.h
-- Installing: /usr/local/include/caffe2/operators/relu_op.h
-- Installing: /usr/local/include/caffe2/operators/remove_data_blocks_op.h
-- Installing: /usr/local/include/caffe2/operators/replace_nan_op.h
-- Installing: /usr/local/include/caffe2/operators/reshape_op.h
-- Installing: /usr/local/include/caffe2/operators/resize_op.h
-- Installing: /usr/local/include/caffe2/operators/reverse_packed_segs_op.h
-- Installing: /usr/local/include/caffe2/operators/roi_pool_op.h
-- Installing: /usr/local/include/caffe2/operators/rowmul_op.h
-- Installing: /usr/local/include/caffe2/operators/scale_op.h
-- Installing: /usr/local/include/caffe2/operators/segment_reduction_op.h
-- Installing: /usr/local/include/caffe2/operators/sequence_ops.h
-- Installing: /usr/local/include/caffe2/operators/shape_op.h
-- Installing: /usr/local/include/caffe2/operators/sinusoid_position_encoding_op.h
-- Installing: /usr/local/include/caffe2/operators/slice_op.h
-- Installing: /usr/local/include/caffe2/operators/softmax_op.h
-- Installing: /usr/local/include/caffe2/operators/softmax_shared.h
-- Installing: /usr/local/include/caffe2/operators/softmax_with_loss_op.h
-- Installing: /usr/local/include/caffe2/operators/softplus_op.h
-- Installing: /usr/local/include/caffe2/operators/space_batch_op.h
-- Installing: /usr/local/include/caffe2/operators/sparse_to_dense_mask_op.h
-- Installing: /usr/local/include/caffe2/operators/sparse_to_dense_op.h
-- Installing: /usr/local/include/caffe2/operators/spatial_batch_norm_op.h
-- Installing: /usr/local/include/caffe2/operators/spatial_softmax_with_loss_op.h
-- Installing: /usr/local/include/caffe2/operators/square_root_divide_op.h
-- Installing: /usr/local/include/caffe2/operators/stop_gradient.h
-- Installing: /usr/local/include/caffe2/operators/string_ops.h
-- Installing: /usr/local/include/caffe2/operators/summarize_op.h
-- Installing: /usr/local/include/caffe2/operators/tensor_protos_db_input.h
-- Installing: /usr/local/include/caffe2/operators/text_file_reader_utils.h
-- Installing: /usr/local/include/caffe2/operators/tile_op.h
-- Installing: /usr/local/include/caffe2/operators/top_k.h
-- Installing: /usr/local/include/caffe2/operators/transpose_op.h
-- Installing: /usr/local/include/caffe2/operators/tt_linear_op.h
-- Installing: /usr/local/include/caffe2/operators/utility_ops.h
-- Installing: /usr/local/include/caffe2/operators/while_op.h
-- Installing: /usr/local/include/caffe2/operators/zero_gradient_op.h
-- Installing: /usr/local/include/caffe2/perfkernels
-- Installing: /usr/local/include/caffe2/perfkernels/common.h
-- Installing: /usr/local/include/caffe2/perfkernels/cvtsh_ss_bugfix.h
-- Installing: /usr/local/include/caffe2/perfkernels/embedding_lookup.h
-- Installing: /usr/local/include/caffe2/perfkernels/typed_axpy.h
-- Installing: /usr/local/include/caffe2/proto
-- Installing: /usr/local/include/caffe2/python
-- Installing: /usr/local/include/caffe2/python/docs
-- Installing: /usr/local/include/caffe2/python/examples
-- Installing: /usr/local/include/caffe2/python/helpers
-- Installing: /usr/local/include/caffe2/python/layers
-- Installing: /usr/local/include/caffe2/python/mint
-- Installing: /usr/local/include/caffe2/python/mint/static
-- Installing: /usr/local/include/caffe2/python/mint/static/css
-- Installing: /usr/local/include/caffe2/python/mint/templates
-- Installing: /usr/local/include/caffe2/python/mkl
-- Installing: /usr/local/include/caffe2/python/modeling
-- Installing: /usr/local/include/caffe2/python/models
-- Installing: /usr/local/include/caffe2/python/models/seq2seq
-- Installing: /usr/local/include/caffe2/python/operator_test
-- Installing: /usr/local/include/caffe2/python/predictor
-- Installing: /usr/local/include/caffe2/python/pybind_state.h
-- Installing: /usr/local/include/caffe2/python/rnn
-- Installing: /usr/local/include/caffe2/python/tutorials
-- Installing: /usr/local/include/caffe2/python/tutorials/experimental
-- Installing: /usr/local/include/caffe2/python/tutorials/images
-- Installing: /usr/local/include/caffe2/queue
-- Installing: /usr/local/include/caffe2/queue/blobs_queue.h
-- Installing: /usr/local/include/caffe2/queue/blobs_queue_db.h
-- Installing: /usr/local/include/caffe2/queue/queue_ops.h
-- Installing: /usr/local/include/caffe2/queue/rebatching_queue.h
-- Installing: /usr/local/include/caffe2/queue/rebatching_queue_ops.h
-- Installing: /usr/local/include/caffe2/sgd
-- Installing: /usr/local/include/caffe2/sgd/adagrad_op.h
-- Installing: /usr/local/include/caffe2/sgd/adam_op.h
-- Installing: /usr/local/include/caffe2/sgd/ftrl_op.h
-- Installing: /usr/local/include/caffe2/sgd/iter_op.h
-- Installing: /usr/local/include/caffe2/sgd/learning_rate_functors.h
-- Installing: /usr/local/include/caffe2/sgd/learning_rate_op.h
-- Installing: /usr/local/include/caffe2/sgd/momentum_sgd_op.h
-- Installing: /usr/local/include/caffe2/sgd/rmsprop_op.h
-- Installing: /usr/local/include/caffe2/sgd/yellowfin_op.h
-- Installing: /usr/local/include/caffe2/test
-- Installing: /usr/local/include/caffe2/test/assets
-- Installing: /usr/local/include/caffe2/transforms
-- Installing: /usr/local/include/caffe2/transforms/common_subexpression_elimination.h
-- Installing: /usr/local/include/caffe2/transforms/conv_to_nnpack_transform.h
-- Installing: /usr/local/include/caffe2/transforms/pattern_net_transform.h
-- Installing: /usr/local/include/caffe2/transforms/single_op_transform.h
-- Installing: /usr/local/include/caffe2/utils
-- Installing: /usr/local/include/caffe2/utils/cast.h
-- Installing: /usr/local/include/caffe2/utils/cblas.h
-- Installing: /usr/local/include/caffe2/utils/conversions.h
-- Installing: /usr/local/include/caffe2/utils/cpu_neon.h
-- Installing: /usr/local/include/caffe2/utils/cpuid.h
-- Installing: /usr/local/include/caffe2/utils/fixed_divisor.h
-- Installing: /usr/local/include/caffe2/utils/math-detail.h
-- Installing: /usr/local/include/caffe2/utils/math.h
-- Installing: /usr/local/include/caffe2/utils/murmur_hash3.h
-- Installing: /usr/local/include/caffe2/utils/proto_utils.h
-- Installing: /usr/local/include/caffe2/utils/signal_handler.h
-- Installing: /usr/local/include/caffe2/utils/simple_queue.h
-- Installing: /usr/local/include/caffe2/utils/smart_tensor_printer.h
-- Installing: /usr/local/include/caffe2/utils/string_utils.h
-- Installing: /usr/local/include/caffe2/utils/thread_pool.h
-- Installing: /usr/local/include/caffe2/utils/threadpool
-- Installing: /usr/local/include/caffe2/utils/threadpool/ThreadPool.h
-- Installing: /usr/local/include/caffe2/utils/threadpool/ThreadPoolCommon.h
-- Installing: /usr/local/include/caffe2/utils/threadpool/WorkersPool.h
-- Installing: /usr/local/include/caffe2/utils/threadpool/pthreadpool.h
-- Installing: /usr/local/include/caffe2/utils/threadpool/pthreadpool_impl.h
-- Installing: /usr/local/include/caffe2/utils/zmq_helper.h
-- Installing: /usr/local/include/caffe2/video
-- Installing: /usr/local/include/caffe2/video/video_decoder.h
-- Installing: /usr/local/include/caffe2/video/video_input_op.h
-- Installing: /usr/local/include/caffe2/video/video_io.h
-- Installing: /usr/local/include/caffe2/core/macros.h
-- Installing: /usr/local/lib/libCaffe2_GPU.so
-- Set runtime path of "/usr/local/lib/libCaffe2_GPU.so" to ""
-- Installing: /usr/local/test/blob_test
-- Set runtime path of "/usr/local/test/blob_test" to ""
-- Installing: /usr/local/test/context_test
-- Set runtime path of "/usr/local/test/context_test" to ""
-- Installing: /usr/local/test/event_test
-- Set runtime path of "/usr/local/test/event_test" to ""
-- Installing: /usr/local/test/graph_test
-- Set runtime path of "/usr/local/test/graph_test" to ""
-- Installing: /usr/local/test/init_test
-- Set runtime path of "/usr/local/test/init_test" to ""
-- Installing: /usr/local/test/logging_test
-- Set runtime path of "/usr/local/test/logging_test" to ""
-- Installing: /usr/local/test/net_test
-- Set runtime path of "/usr/local/test/net_test" to ""
-- Installing: /usr/local/test/observer_test
-- Set runtime path of "/usr/local/test/observer_test" to ""
-- Installing: /usr/local/test/operator_schema_test
-- Set runtime path of "/usr/local/test/operator_schema_test" to ""
-- Installing: /usr/local/test/operator_test
-- Set runtime path of "/usr/local/test/operator_test" to ""
-- Installing: /usr/local/test/parallel_net_test
-- Set runtime path of "/usr/local/test/parallel_net_test" to ""
-- Installing: /usr/local/test/predictor_test
-- Set runtime path of "/usr/local/test/predictor_test" to ""
-- Installing: /usr/local/test/registry_test
-- Set runtime path of "/usr/local/test/registry_test" to ""
-- Installing: /usr/local/test/stats_test
-- Set runtime path of "/usr/local/test/stats_test" to ""
-- Installing: /usr/local/test/timer_test
-- Set runtime path of "/usr/local/test/timer_test" to ""
-- Installing: /usr/local/test/transform_test
-- Set runtime path of "/usr/local/test/transform_test" to ""
-- Installing: /usr/local/test/typeid_test
-- Set runtime path of "/usr/local/test/typeid_test" to ""
-- Installing: /usr/local/test/workspace_test
-- Set runtime path of "/usr/local/test/workspace_test" to ""
-- Installing: /usr/local/test/boolean_unmask_ops_test
-- Set runtime path of "/usr/local/test/boolean_unmask_ops_test" to ""
-- Installing: /usr/local/test/conv_transpose_op_mobile_test
-- Set runtime path of "/usr/local/test/conv_transpose_op_mobile_test" to ""
-- Installing: /usr/local/test/elementwise_op_test
-- Set runtime path of "/usr/local/test/elementwise_op_test" to ""
-- Installing: /usr/local/test/fully_connected_op_test
-- Set runtime path of "/usr/local/test/fully_connected_op_test" to ""
-- Installing: /usr/local/test/string_ops_test
-- Set runtime path of "/usr/local/test/string_ops_test" to ""
-- Installing: /usr/local/test/text_file_reader_utils_test
-- Set runtime path of "/usr/local/test/text_file_reader_utils_test" to ""
-- Installing: /usr/local/test/utility_ops_test
-- Set runtime path of "/usr/local/test/utility_ops_test" to ""
-- Installing: /usr/local/test/common_subexpression_elimination_test
-- Set runtime path of "/usr/local/test/common_subexpression_elimination_test" to ""
-- Installing: /usr/local/test/conv_to_nnpack_transform_test
-- Set runtime path of "/usr/local/test/conv_to_nnpack_transform_test" to ""
-- Installing: /usr/local/test/pattern_net_transform_test
-- Set runtime path of "/usr/local/test/pattern_net_transform_test" to ""
-- Installing: /usr/local/test/cpuid_test
-- Set runtime path of "/usr/local/test/cpuid_test" to ""
-- Installing: /usr/local/test/fatal_signal_asan_no_sig_test
-- Set runtime path of "/usr/local/test/fatal_signal_asan_no_sig_test" to ""
-- Installing: /usr/local/test/fixed_divisor_test
-- Set runtime path of "/usr/local/test/fixed_divisor_test" to ""
-- Installing: /usr/local/test/math_test
-- Set runtime path of "/usr/local/test/math_test" to ""
-- Installing: /usr/local/test/proto_utils_test
-- Set runtime path of "/usr/local/test/proto_utils_test" to ""
-- Installing: /usr/local/test/simple_queue_test
-- Set runtime path of "/usr/local/test/simple_queue_test" to ""
-- Installing: /usr/local/test/smart_tensor_printer_test
-- Set runtime path of "/usr/local/test/smart_tensor_printer_test" to ""
-- Installing: /usr/local/test/blob_gpu_test
-- Set runtime path of "/usr/local/test/blob_gpu_test" to ""
-- Installing: /usr/local/test/context_gpu_test
-- Set runtime path of "/usr/local/test/context_gpu_test" to ""
-- Installing: /usr/local/test/event_gpu_test
-- Set runtime path of "/usr/local/test/event_gpu_test" to ""
-- Installing: /usr/local/test/operator_gpu_test
-- Set runtime path of "/usr/local/test/operator_gpu_test" to ""
-- Installing: /usr/local/test/conv_op_cache_cudnn_test
-- Set runtime path of "/usr/local/test/conv_op_cache_cudnn_test" to ""
-- Installing: /usr/local/test/elementwise_op_gpu_test
-- Set runtime path of "/usr/local/test/elementwise_op_gpu_test" to ""
-- Installing: /usr/local/test/fully_connected_op_gpu_test
-- Set runtime path of "/usr/local/test/fully_connected_op_gpu_test" to ""
-- Installing: /usr/local/test/operator_fallback_gpu_test
-- Set runtime path of "/usr/local/test/operator_fallback_gpu_test" to ""
-- Installing: /usr/local/test/reshape_op_gpu_test
-- Set runtime path of "/usr/local/test/reshape_op_gpu_test" to ""
-- Installing: /usr/local/test/utility_ops_gpu_test
-- Set runtime path of "/usr/local/test/utility_ops_gpu_test" to ""
-- Installing: /usr/local/test/math_gpu_test
-- Set runtime path of "/usr/local/test/math_gpu_test" to ""
-- Installing: /usr/local/caffe2/python/caffe2_pybind11_state.so
-- Set runtime path of "/usr/local/caffe2/python/caffe2_pybind11_state.so" to ""
-- Installing: /usr/local/caffe2/python/caffe2_pybind11_state_gpu.so
-- Set runtime path of "/usr/local/caffe2/python/caffe2_pybind11_state_gpu.so" to ""
-- Up-to-date: /usr/local/./caffe2
-- Installing: /usr/local/./caffe2/CMakeFiles
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/sgd
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/utils
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/contrib
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/contrib/gloo
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/contrib/nccl
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/cuda_rtc
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/db
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/distributed
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/queue
-- Installing: /usr/local/./caffe2/CMakeFiles/python_copy_files.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/caffe2_pybind11_state_gpu.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/caffe2_pybind11_state_gpu.dir/python
-- Installing: /usr/local/./caffe2/CMakeFiles/caffe2_pybind11_state.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/caffe2_pybind11_state.dir/python
-- Installing: /usr/local/./caffe2/CMakeFiles/cpuid_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/cpuid_test.dir/utils
-- Installing: /usr/local/./caffe2/CMakeFiles/fatal_signal_asan_no_sig_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/fatal_signal_asan_no_sig_test.dir/utils
-- Installing: /usr/local/./caffe2/CMakeFiles/typeid_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/typeid_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/timer_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/timer_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/operator_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/operator_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/conv_transpose_op_mobile_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/conv_transpose_op_mobile_test.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/conv_to_nnpack_transform_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/conv_to_nnpack_transform_test.dir/transforms
-- Installing: /usr/local/./caffe2/CMakeFiles/smart_tensor_printer_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/smart_tensor_printer_test.dir/utils
-- Installing: /usr/local/./caffe2/CMakeFiles/registry_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/registry_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/workspace_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/workspace_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/context_gpu_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/context_gpu_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/operator_fallback_gpu_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/operator_fallback_gpu_test.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/contrib
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/contrib/gloo
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/db
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/distributed
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/perfkernels
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/queue
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/sgd
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/transforms
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/utils
-- Installing: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/utils/threadpool
-- Installing: /usr/local/./caffe2/CMakeFiles/blob_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/blob_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/parallel_net_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/parallel_net_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/fixed_divisor_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/fixed_divisor_test.dir/utils
-- Installing: /usr/local/./caffe2/CMakeFiles/init_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/init_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/transform_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/transform_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/event_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/event_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/graph_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/graph_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/string_ops_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/string_ops_test.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/predictor_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/predictor_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/observer_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/observer_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/logging_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/logging_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/net_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/net_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/elementwise_op_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/elementwise_op_test.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/boolean_unmask_ops_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/boolean_unmask_ops_test.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/conv_op_cache_cudnn_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/conv_op_cache_cudnn_test.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/reshape_op_gpu_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/reshape_op_gpu_test.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/operator_schema_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/operator_schema_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/fully_connected_op_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/fully_connected_op_test.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/simple_queue_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/simple_queue_test.dir/utils
-- Installing: /usr/local/./caffe2/CMakeFiles/text_file_reader_utils_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/text_file_reader_utils_test.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/math_gpu_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/math_gpu_test.dir/utils
-- Installing: /usr/local/./caffe2/CMakeFiles/stats_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/stats_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/event_gpu_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/event_gpu_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/utility_ops_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/utility_ops_test.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/utility_ops_gpu_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/utility_ops_gpu_test.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/context_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/context_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/common_subexpression_elimination_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/common_subexpression_elimination_test.dir/transforms
-- Installing: /usr/local/./caffe2/CMakeFiles/proto_utils_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/proto_utils_test.dir/utils
-- Installing: /usr/local/./caffe2/CMakeFiles/pattern_net_transform_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/pattern_net_transform_test.dir/transforms
-- Installing: /usr/local/./caffe2/CMakeFiles/math_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/math_test.dir/utils
-- Installing: /usr/local/./caffe2/CMakeFiles/blob_gpu_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/blob_gpu_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/operator_gpu_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/operator_gpu_test.dir/core
-- Installing: /usr/local/./caffe2/CMakeFiles/elementwise_op_gpu_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/elementwise_op_gpu_test.dir/operators
-- Installing: /usr/local/./caffe2/CMakeFiles/fully_connected_op_gpu_test.dir
-- Installing: /usr/local/./caffe2/CMakeFiles/fully_connected_op_gpu_test.dir/operators
-- Installing: /usr/local/./caffe2/proto
-- Installing: /usr/local/./caffe2/proto/CMakeFiles
-- Installing: /usr/local/./caffe2/proto/CMakeFiles/Caffe2_PROTO.dir
-- Installing: /usr/local/./caffe2/proto/__init__.py
-- Installing: /usr/local/./caffe2/proto/prof_dag_pb2.py
-- Installing: /usr/local/./caffe2/proto/caffe2_pb2.py
-- Installing: /usr/local/./caffe2/proto/caffe2_legacy_pb2.py
-- Installing: /usr/local/./caffe2/proto/hsm_pb2.py
-- Installing: /usr/local/./caffe2/proto/metanet_pb2.py
-- Installing: /usr/local/./caffe2/proto/predictor_consts_pb2.py
-- Installing: /usr/local/./caffe2/contrib
-- Installing: /usr/local/./caffe2/contrib/CMakeFiles
-- Installing: /usr/local/./caffe2/contrib/gloo
-- Installing: /usr/local/./caffe2/contrib/gloo/CMakeFiles
-- Installing: /usr/local/./caffe2/contrib/gloo/__init__.py
-- Installing: /usr/local/./caffe2/contrib/gloo/gloo_test.py
-- Installing: /usr/local/./caffe2/contrib/nccl
-- Installing: /usr/local/./caffe2/contrib/nccl/CMakeFiles
-- Installing: /usr/local/./caffe2/contrib/nccl/__init__.py
-- Installing: /usr/local/./caffe2/contrib/nccl/nccl_ops_test.py
-- Installing: /usr/local/./caffe2/contrib/nnpack
-- Installing: /usr/local/./caffe2/contrib/nnpack/CMakeFiles
-- Installing: /usr/local/./caffe2/contrib/nnpack/__init__.py
-- Installing: /usr/local/./caffe2/contrib/nnpack/nnpack_ops_test.py
-- Installing: /usr/local/./caffe2/contrib/observers
-- Installing: /usr/local/./caffe2/contrib/observers/CMakeFiles
-- Installing: /usr/local/./caffe2/contrib/shm_mutex
-- Installing: /usr/local/./caffe2/contrib/shm_mutex/CMakeFiles
-- Installing: /usr/local/./caffe2/contrib/__init__.py
-- Installing: /usr/local/./caffe2/contrib/prof
-- Installing: /usr/local/./caffe2/contrib/prof/__init__.py
-- Installing: /usr/local/./caffe2/contrib/prof/cuda_profile_ops_test.py
-- Installing: /usr/local/./caffe2/contrib/prof/htrace_to_chrome.py
-- Installing: /usr/local/./caffe2/contrib/torch
-- Installing: /usr/local/./caffe2/contrib/torch/__init__.py
-- Installing: /usr/local/./caffe2/contrib/torch/th_ops_test.py
-- Installing: /usr/local/./caffe2/contrib/torch/torch_ops_test.py
-- Installing: /usr/local/./caffe2/contrib/warpctc
-- Installing: /usr/local/./caffe2/contrib/warpctc/__init__.py
-- Installing: /usr/local/./caffe2/contrib/warpctc/ctc_ops_test.py
-- Installing: /usr/local/./caffe2/core
-- Installing: /usr/local/./caffe2/core/CMakeFiles
-- Installing: /usr/local/./caffe2/cuda_rtc
-- Installing: /usr/local/./caffe2/cuda_rtc/CMakeFiles
-- Installing: /usr/local/./caffe2/db
-- Installing: /usr/local/./caffe2/db/CMakeFiles
-- Installing: /usr/local/./caffe2/distributed
-- Installing: /usr/local/./caffe2/distributed/CMakeFiles
-- Installing: /usr/local/./caffe2/distributed/__init__.py
-- Installing: /usr/local/./caffe2/distributed/file_store_handler_op_test.py
-- Installing: /usr/local/./caffe2/distributed/redis_store_handler_op_test.py
-- Installing: /usr/local/./caffe2/distributed/store_ops_test_util.py
-- Installing: /usr/local/./caffe2/image
-- Installing: /usr/local/./caffe2/image/CMakeFiles
-- Installing: /usr/local/./caffe2/video
-- Installing: /usr/local/./caffe2/video/CMakeFiles
-- Installing: /usr/local/./caffe2/mkl
-- Installing: /usr/local/./caffe2/mkl/CMakeFiles
-- Installing: /usr/local/./caffe2/mobile
-- Installing: /usr/local/./caffe2/mobile/CMakeFiles
-- Installing: /usr/local/./caffe2/mobile/contrib
-- Installing: /usr/local/./caffe2/mobile/contrib/CMakeFiles
-- Installing: /usr/local/./caffe2/mobile/contrib/ios
-- Installing: /usr/local/./caffe2/mobile/contrib/ios/CMakeFiles
-- Installing: /usr/local/./caffe2/mobile/contrib/opengl
-- Installing: /usr/local/./caffe2/mobile/contrib/opengl/CMakeFiles
-- Installing: /usr/local/./caffe2/mpi
-- Installing: /usr/local/./caffe2/mpi/CMakeFiles
-- Installing: /usr/local/./caffe2/operators
-- Installing: /usr/local/./caffe2/operators/CMakeFiles
-- Installing: /usr/local/./caffe2/perfkernels
-- Installing: /usr/local/./caffe2/perfkernels/CMakeFiles
-- Installing: /usr/local/./caffe2/perfkernels/CMakeFiles/Caffe2_perfkernels_avx2.dir
-- Installing: /usr/local/./caffe2/perfkernels/CMakeFiles/Caffe2_perfkernels_avx.dir
-- Installing: /usr/local/./caffe2/perfkernels/__init__.py
-- Installing: /usr/local/./caffe2/perfkernels/hp_emblookup_codegen.py
-- Up-to-date: /usr/local/./caffe2/python
-- Installing: /usr/local/./caffe2/python/CMakeFiles
-- Installing: /usr/local/./caffe2/python/__init__.py
-- Installing: /usr/local/./caffe2/python/docs
-- Installing: /usr/local/./caffe2/python/docs/__init__.py
-- Installing: /usr/local/./caffe2/python/docs/formatter.py
-- Installing: /usr/local/./caffe2/python/docs/generator.py
-- Installing: /usr/local/./caffe2/python/docs/github.py
-- Installing: /usr/local/./caffe2/python/docs/parser.py
-- Installing: /usr/local/./caffe2/python/examples
-- Installing: /usr/local/./caffe2/python/examples/__init__.py
-- Installing: /usr/local/./caffe2/python/examples/char_rnn.py
-- Installing: /usr/local/./caffe2/python/examples/lmdb_create_example.py
-- Installing: /usr/local/./caffe2/python/examples/resnet50_trainer.py
-- Installing: /usr/local/./caffe2/python/helpers
-- Installing: /usr/local/./caffe2/python/helpers/__init__.py
-- Installing: /usr/local/./caffe2/python/helpers/algebra.py
-- Installing: /usr/local/./caffe2/python/helpers/arg_scope.py
-- Installing: /usr/local/./caffe2/python/helpers/array_helpers.py
-- Installing: /usr/local/./caffe2/python/helpers/conv.py
-- Installing: /usr/local/./caffe2/python/helpers/dropout.py
-- Installing: /usr/local/./caffe2/python/helpers/elementwise_linear.py
-- Installing: /usr/local/./caffe2/python/helpers/fc.py
-- Installing: /usr/local/./caffe2/python/helpers/nonlinearity.py
-- Installing: /usr/local/./caffe2/python/helpers/normalization.py
-- Installing: /usr/local/./caffe2/python/helpers/pooling.py
-- Installing: /usr/local/./caffe2/python/helpers/tools.py
-- Installing: /usr/local/./caffe2/python/helpers/train.py
-- Installing: /usr/local/./caffe2/python/layers
-- Installing: /usr/local/./caffe2/python/layers/__init__.py
-- Installing: /usr/local/./caffe2/python/layers/add_bias.py
-- Installing: /usr/local/./caffe2/python/layers/arc_cosine_feature_map.py
-- Installing: /usr/local/./caffe2/python/layers/batch_distill_lr_loss.py
-- Installing: /usr/local/./caffe2/python/layers/batch_lr_loss.py
-- Installing: /usr/local/./caffe2/python/layers/batch_mse_loss.py
-- Installing: /usr/local/./caffe2/python/layers/batch_normalization.py
-- Installing: /usr/local/./caffe2/python/layers/batch_sigmoid_cross_entropy_loss.py
-- Installing: /usr/local/./caffe2/python/layers/batch_softmax_loss.py
-- Installing: /usr/local/./caffe2/python/layers/build_index.py
-- Installing: /usr/local/./caffe2/python/layers/concat.py
-- Installing: /usr/local/./caffe2/python/layers/conv.py
-- Installing: /usr/local/./caffe2/python/layers/dropout.py
-- Installing: /usr/local/./caffe2/python/layers/fc.py
-- Installing: /usr/local/./caffe2/python/layers/fc_without_bias.py
-- Installing: /usr/local/./caffe2/python/layers/feature_sparse_to_dense.py
-- Installing: /usr/local/./caffe2/python/layers/functional.py
-- Installing: /usr/local/./caffe2/python/layers/gather_record.py
-- Installing: /usr/local/./caffe2/python/layers/last_n_window_collector.py
-- Installing: /usr/local/./caffe2/python/layers/layers.py
-- Installing: /usr/local/./caffe2/python/layers/merge_id_lists.py
-- Installing: /usr/local/./caffe2/python/layers/pairwise_dot_product.py
-- Installing: /usr/local/./caffe2/python/layers/position_weighted.py
-- Installing: /usr/local/./caffe2/python/layers/random_fourier_features.py
-- Installing: /usr/local/./caffe2/python/layers/reservoir_sampling.py
-- Installing: /usr/local/./caffe2/python/layers/sampling_train.py
-- Installing: /usr/local/./caffe2/python/layers/sampling_trainable_mixin.py
-- Installing: /usr/local/./caffe2/python/layers/select_record_by_context.py
-- Installing: /usr/local/./caffe2/python/layers/semi_random_features.py
-- Installing: /usr/local/./caffe2/python/layers/sparse_feature_hash.py
-- Installing: /usr/local/./caffe2/python/layers/sparse_lookup.py
-- Installing: /usr/local/./caffe2/python/layers/split.py
-- Installing: /usr/local/./caffe2/python/layers/tags.py
-- Installing: /usr/local/./caffe2/python/layers/uniform_sampling.py
-- Installing: /usr/local/./caffe2/python/mint
-- Installing: /usr/local/./caffe2/python/mint/__init__.py
-- Installing: /usr/local/./caffe2/python/mint/app.py
-- Installing: /usr/local/./caffe2/python/mkl
-- Installing: /usr/local/./caffe2/python/mkl/__init__.py
-- Installing: /usr/local/./caffe2/python/mkl/convnet_benchmarks.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_LRN_op_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_LRN_speed_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_conv_op_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_copy_op_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_elementwise_sum_op_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_fc_op_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_fc_speed_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_fill_op_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_pool_op_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_pool_speed_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_relu_op_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_sbn_op_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_sbn_speed_test.py
-- Installing: /usr/local/./caffe2/python/mkl/mkl_speed_test.py
-- Installing: /usr/local/./caffe2/python/mkl/rewrite_graph.py
-- Installing: /usr/local/./caffe2/python/mkl/rewrite_graph_test.py
-- Installing: /usr/local/./caffe2/python/modeling
-- Installing: /usr/local/./caffe2/python/modeling/__init__.py
-- Installing: /usr/local/./caffe2/python/modeling/initializers.py
-- Installing: /usr/local/./caffe2/python/modeling/initializers_test.py
-- Installing: /usr/local/./caffe2/python/modeling/parameter_info.py
-- Installing: /usr/local/./caffe2/python/modeling/parameter_sharing.py
-- Installing: /usr/local/./caffe2/python/modeling/parameter_sharing_test.py
-- Installing: /usr/local/./caffe2/python/models
-- Installing: /usr/local/./caffe2/python/models/__init__.py
-- Installing: /usr/local/./caffe2/python/models/seq2seq
-- Installing: /usr/local/./caffe2/python/models/seq2seq/__init__.py
-- Installing: /usr/local/./caffe2/python/models/seq2seq/beam_search.py
-- Installing: /usr/local/./caffe2/python/models/seq2seq/seq2seq_beam_search_test.py
-- Installing: /usr/local/./caffe2/python/models/seq2seq/seq2seq_model_helper.py
-- Installing: /usr/local/./caffe2/python/models/seq2seq/seq2seq_model_helper_test.py
-- Installing: /usr/local/./caffe2/python/models/seq2seq/seq2seq_util.py
-- Installing: /usr/local/./caffe2/python/models/seq2seq/train.py
-- Installing: /usr/local/./caffe2/python/models/seq2seq/translate.py
-- Installing: /usr/local/./caffe2/python/models/__sym_init__.py
-- Installing: /usr/local/./caffe2/python/models/download.py
-- Installing: /usr/local/./caffe2/python/models/resnet.py
-- Installing: /usr/local/./caffe2/python/models/resnet_test.py
-- Installing: /usr/local/./caffe2/python/operator_test
-- Installing: /usr/local/./caffe2/python/operator_test/__init__.py
-- Installing: /usr/local/./caffe2/python/operator_test/activation_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/adagrad_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/adam_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/apmeter_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/atomic_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/batch_box_cox_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/blobs_queue_db_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/boolean_mask_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/boolean_unmask_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/channel_shuffle_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/checkpoint_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/clip_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/concat_split_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/conditional_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/conv_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/conv_transpose_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/copy_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/cosine_embedding_criterion_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/counter_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/crf_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/cross_entropy_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/cudnn_recurrent_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/dataset_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/distance_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/dropout_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/duplicate_operands_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/elementwise_linear_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/elementwise_logical_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/elementwise_op_broadcast_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/elementwise_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/emptysample_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/extend_tensor_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/fc_operator_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/filler_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/find_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/gather_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/gather_ranges_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/given_tensor_fill_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/group_conv_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/gru_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/hsm_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/im2col_col2im_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/image_input_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/index_hash_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/index_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/instance_norm_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/layer_norm_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/leaky_relu_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/lengths_tile_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/lengths_top_k_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/loss_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/lpnorm_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/map_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/margin_ranking_criterion_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/matmul_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/merge_id_lists_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/mkl_conv_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/mkl_packed_fc_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/mkl_speed_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/momentum_sgd_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/mpi_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/normalize_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/one_hot_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/pack_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/pack_rnn_sequence_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/pad_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/partition_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/piecewise_linear_transform_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/pooling_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/pow_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/prepend_dim_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/python_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/rank_loss_operator_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/rebatching_queue_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/record_queue_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/recurrent_net_executor_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/recurrent_network_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/reduce_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/reduction_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/relu_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/reshape_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/resize_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/rnn_cell_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/segment_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/sequence_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/shape_inference_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/sinusoid_position_encoding_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/softmax_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/softplus_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/sparse_gradient_checker_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/sparse_lengths_sum_benchmark.py
-- Installing: /usr/local/./caffe2/python/operator_test/sparse_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/sparse_to_dense_mask_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/spatial_bn_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/specialized_segment_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/square_root_divide_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/stats_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/string_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/text_file_reader_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/tile_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/top_k_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/unique_uniform_fill_op_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/utility_ops_test.py
-- Installing: /usr/local/./caffe2/python/operator_test/video_input_op_test.py
-- Installing: /usr/local/./caffe2/python/predictor
-- Installing: /usr/local/./caffe2/python/predictor/__init__.py
-- Installing: /usr/local/./caffe2/python/predictor/mobile_exporter.py
-- Installing: /usr/local/./caffe2/python/predictor/mobile_exporter_test.py
-- Installing: /usr/local/./caffe2/python/predictor/predictor_exporter.py
-- Installing: /usr/local/./caffe2/python/predictor/predictor_exporter_test.py
-- Installing: /usr/local/./caffe2/python/predictor/predictor_py_utils.py
-- Installing: /usr/local/./caffe2/python/predictor/serde.py
-- Installing: /usr/local/./caffe2/python/rnn
-- Installing: /usr/local/./caffe2/python/rnn/__init__.py
-- Installing: /usr/local/./caffe2/python/rnn/lstm_comparison.py
-- Installing: /usr/local/./caffe2/python/rnn/rnn_cell_test_util.py
-- Installing: /usr/local/./caffe2/python/tutorials
-- Installing: /usr/local/./caffe2/python/tutorials/__init__.py
-- Installing: /usr/local/./caffe2/python/tutorials/helpers.py
-- Installing: /usr/local/./caffe2/python/test_util.py
-- Installing: /usr/local/./caffe2/python/text_file_reader.py
-- Installing: /usr/local/./caffe2/python/_import_c_extension.py
-- Installing: /usr/local/./caffe2/python/allcompare_test.py
-- Installing: /usr/local/./caffe2/python/attention.py
-- Installing: /usr/local/./caffe2/python/benchmark_generator.py
-- Installing: /usr/local/./caffe2/python/binarysize.py
-- Installing: /usr/local/./caffe2/python/brew.py
-- Installing: /usr/local/./caffe2/python/brew_test.py
-- Installing: /usr/local/./caffe2/python/build.py
-- Installing: /usr/local/./caffe2/python/caffe_translator.py
-- Installing: /usr/local/./caffe2/python/caffe_translator_test.py
-- Installing: /usr/local/./caffe2/python/checkpoint.py
-- Installing: /usr/local/./caffe2/python/checkpoint_test.py
-- Installing: /usr/local/./caffe2/python/cnn.py
-- Installing: /usr/local/./caffe2/python/context.py
-- Installing: /usr/local/./caffe2/python/context_test.py
-- Installing: /usr/local/./caffe2/python/control.py
-- Installing: /usr/local/./caffe2/python/control_ops_util.py
-- Installing: /usr/local/./caffe2/python/control_test.py
-- Installing: /usr/local/./caffe2/python/convnet_benchmarks.py
-- Installing: /usr/local/./caffe2/python/convnet_benchmarks_test.py
-- Installing: /usr/local/./caffe2/python/core.py
-- Installing: /usr/local/./caffe2/python/core_gradients_test.py
-- Installing: /usr/local/./caffe2/python/core_test.py
-- Installing: /usr/local/./caffe2/python/crf.py
-- Installing: /usr/local/./caffe2/python/data_parallel_model.py
-- Installing: /usr/local/./caffe2/python/data_parallel_model_test.py
-- Installing: /usr/local/./caffe2/python/data_workers.py
-- Installing: /usr/local/./caffe2/python/data_workers_test.py
-- Installing: /usr/local/./caffe2/python/dataio.py
-- Installing: /usr/local/./caffe2/python/dataio_test.py
-- Installing: /usr/local/./caffe2/python/dataset.py
-- Installing: /usr/local/./caffe2/python/db_test.py
-- Installing: /usr/local/./caffe2/python/device_checker.py
-- Installing: /usr/local/./caffe2/python/dyndep.py
-- Installing: /usr/local/./caffe2/python/embedding_generation_benchmark.py
-- Installing: /usr/local/./caffe2/python/experiment_util.py
-- Installing: /usr/local/./caffe2/python/extension_loader.py
-- Installing: /usr/local/./caffe2/python/gradient_check_test.py
-- Installing: /usr/local/./caffe2/python/gradient_checker.py
-- Installing: /usr/local/./caffe2/python/gru_cell.py
-- Installing: /usr/local/./caffe2/python/hsm_util.py
-- Installing: /usr/local/./caffe2/python/hypothesis_test.py
-- Installing: /usr/local/./caffe2/python/hypothesis_test_util.py
-- Installing: /usr/local/./caffe2/python/layer_model_helper.py
-- Installing: /usr/local/./caffe2/python/layer_model_instantiator.py
-- Installing: /usr/local/./caffe2/python/layer_parameter_sharing_test.py
-- Installing: /usr/local/./caffe2/python/layer_test_util.py
-- Installing: /usr/local/./caffe2/python/layers_test.py
-- Installing: /usr/local/./caffe2/python/lengths_reducer_rowwise_8bit_ops_test.py
-- Installing: /usr/local/./caffe2/python/load_save_test.py
-- Installing: /usr/local/./caffe2/python/lstm_benchmark.py
-- Installing: /usr/local/./caffe2/python/memonger.py
-- Installing: /usr/local/./caffe2/python/memonger_test.py
-- Installing: /usr/local/./caffe2/python/mkl_test_util.py
-- Installing: /usr/local/./caffe2/python/model_device_test.py
-- Installing: /usr/local/./caffe2/python/model_helper.py
-- Installing: /usr/local/./caffe2/python/muji.py
-- Installing: /usr/local/./caffe2/python/muji_test.py
-- Installing: /usr/local/./caffe2/python/net_builder.py
-- Installing: /usr/local/./caffe2/python/net_builder_test.py
-- Installing: /usr/local/./caffe2/python/net_drawer.py
-- Installing: /usr/local/./caffe2/python/net_printer.py
-- Installing: /usr/local/./caffe2/python/net_printer_test.py
-- Installing: /usr/local/./caffe2/python/optimizer.py
-- Installing: /usr/local/./caffe2/python/optimizer_context.py
-- Installing: /usr/local/./caffe2/python/optimizer_test.py
-- Installing: /usr/local/./caffe2/python/optimizer_test_util.py
-- Installing: /usr/local/./caffe2/python/parallel_workers.py
-- Installing: /usr/local/./caffe2/python/parallel_workers_test.py
-- Installing: /usr/local/./caffe2/python/parallelize_gpu_bmuf_distributed_test.py
-- Installing: /usr/local/./caffe2/python/pipeline.py
-- Installing: /usr/local/./caffe2/python/pipeline_test.py
-- Installing: /usr/local/./caffe2/python/predictor_constants.py
-- Installing: /usr/local/./caffe2/python/python_op_test.py
-- Installing: /usr/local/./caffe2/python/queue_util.py
-- Installing: /usr/local/./caffe2/python/record_queue.py
-- Installing: /usr/local/./caffe2/python/recurrent.py
-- Installing: /usr/local/./caffe2/python/rnn_cell.py
-- Installing: /usr/local/./caffe2/python/schema.py
-- Installing: /usr/local/./caffe2/python/schema_test.py
-- Installing: /usr/local/./caffe2/python/scope.py
-- Installing: /usr/local/./caffe2/python/scope_test.py
-- Installing: /usr/local/./caffe2/python/session.py
-- Installing: /usr/local/./caffe2/python/session_test.py
-- Installing: /usr/local/./caffe2/python/sparse_to_dense_mask_test.py
-- Installing: /usr/local/./caffe2/python/task.py
-- Installing: /usr/local/./caffe2/python/timeout_guard.py
-- Installing: /usr/local/./caffe2/python/toy_regression_test.py
-- Installing: /usr/local/./caffe2/python/tt_core.py
-- Installing: /usr/local/./caffe2/python/tt_core_test.py
-- Installing: /usr/local/./caffe2/python/utils.py
-- Installing: /usr/local/./caffe2/python/visualize.py
-- Installing: /usr/local/./caffe2/python/workspace.py
-- Installing: /usr/local/./caffe2/python/workspace_test.py
-- Installing: /usr/local/./caffe2/queue
-- Installing: /usr/local/./caffe2/queue/CMakeFiles
-- Installing: /usr/local/./caffe2/sgd
-- Installing: /usr/local/./caffe2/sgd/CMakeFiles
-- Installing: /usr/local/./caffe2/transforms
-- Installing: /usr/local/./caffe2/transforms/CMakeFiles
-- Installing: /usr/local/./caffe2/utils
-- Installing: /usr/local/./caffe2/utils/CMakeFiles
-- Installing: /usr/local/./caffe2/__init__.py
-- Installing: /usr/local/./caffe2/experiments
-- Installing: /usr/local/./caffe2/experiments/__init__.py
-- Installing: /usr/local/./caffe2/experiments/python
-- Installing: /usr/local/./caffe2/experiments/python/__init__.py
-- Installing: /usr/local/./caffe2/experiments/python/SparseTransformer.py
-- Installing: /usr/local/./caffe2/experiments/python/convnet_benchmarks.py
-- Installing: /usr/local/./caffe2/experiments/python/device_reduce_sum_bench.py
-- Installing: /usr/local/./caffe2/experiments/python/funhash_op_test.py
-- Installing: /usr/local/./caffe2/experiments/python/net_construct_bench.py
-- Installing: /usr/local/./caffe2/experiments/python/sparse_funhash_op_test.py
-- Installing: /usr/local/./caffe2/experiments/python/sparse_reshape_op_test.py
-- Installing: /usr/local/./caffe2/experiments/python/tt_contraction_op_test.py
-- Installing: /usr/local/./caffe2/experiments/python/tt_pad_op_test.py
-- Installing: /usr/local/./caffe2/binaries
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/tutorial_blob.dir
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/print_core_object_sizes.dir
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/inspect_gpus.dir
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/predictor_verifier.dir
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/convert_db.dir
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/print_registered_core_operators.dir
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/convert_caffe_image_db.dir
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/db_throughput.dir
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/run_plan.dir
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/make_mnist_db.dir
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/speed_benchmark.dir
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/make_cifar_db.dir
-- Installing: /usr/local/./caffe2/binaries/CMakeFiles/split_db.dir
-- Installing: /usr/local/./caffe2/binaries/binaries
-- Installing: /usr/local/./caffe
-- Installing: /usr/local/./caffe/proto
-- Installing: /usr/local/./caffe/proto/CMakeFiles
-- Installing: /usr/local/./caffe/proto/CMakeFiles/Caffe_PROTO.dir
-- Installing: /usr/local/./caffe/proto/__init__.py
-- Installing: /usr/local/./caffe/proto/caffe_pb2.py
-- Installing: /usr/local/./caffe/__init__.py
-- Up-to-date: /usr/local/./caffe2
-- Up-to-date: /usr/local/./caffe2/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/sgd
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/utils
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/contrib
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/contrib/gloo
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/contrib/nccl
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/cuda_rtc
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/db
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/distributed
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_GPU.dir/queue
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/python_copy_files.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/caffe2_pybind11_state_gpu.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/caffe2_pybind11_state_gpu.dir/python
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/caffe2_pybind11_state.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/caffe2_pybind11_state.dir/python
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/cpuid_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/cpuid_test.dir/utils
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/fatal_signal_asan_no_sig_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/fatal_signal_asan_no_sig_test.dir/utils
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/typeid_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/typeid_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/timer_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/timer_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/operator_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/operator_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/conv_transpose_op_mobile_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/conv_transpose_op_mobile_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/conv_to_nnpack_transform_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/conv_to_nnpack_transform_test.dir/transforms
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/smart_tensor_printer_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/smart_tensor_printer_test.dir/utils
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/registry_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/registry_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/workspace_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/workspace_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/context_gpu_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/context_gpu_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/operator_fallback_gpu_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/operator_fallback_gpu_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/contrib
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/contrib/gloo
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/db
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/distributed
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/perfkernels
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/queue
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/sgd
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/transforms
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/utils
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/Caffe2_CPU.dir/utils/threadpool
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/blob_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/blob_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/parallel_net_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/parallel_net_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/fixed_divisor_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/fixed_divisor_test.dir/utils
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/init_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/init_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/transform_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/transform_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/event_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/event_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/graph_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/graph_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/string_ops_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/string_ops_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/predictor_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/predictor_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/observer_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/observer_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/logging_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/logging_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/net_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/net_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/elementwise_op_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/elementwise_op_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/boolean_unmask_ops_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/boolean_unmask_ops_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/conv_op_cache_cudnn_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/conv_op_cache_cudnn_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/reshape_op_gpu_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/reshape_op_gpu_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/operator_schema_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/operator_schema_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/fully_connected_op_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/fully_connected_op_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/simple_queue_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/simple_queue_test.dir/utils
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/text_file_reader_utils_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/text_file_reader_utils_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/math_gpu_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/math_gpu_test.dir/utils
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/stats_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/stats_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/event_gpu_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/event_gpu_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/utility_ops_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/utility_ops_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/utility_ops_gpu_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/utility_ops_gpu_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/context_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/context_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/common_subexpression_elimination_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/common_subexpression_elimination_test.dir/transforms
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/proto_utils_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/proto_utils_test.dir/utils
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/pattern_net_transform_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/pattern_net_transform_test.dir/transforms
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/math_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/math_test.dir/utils
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/blob_gpu_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/blob_gpu_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/operator_gpu_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/operator_gpu_test.dir/core
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/elementwise_op_gpu_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/elementwise_op_gpu_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/fully_connected_op_gpu_test.dir
-- Up-to-date: /usr/local/./caffe2/CMakeFiles/fully_connected_op_gpu_test.dir/operators
-- Up-to-date: /usr/local/./caffe2/proto
-- Up-to-date: /usr/local/./caffe2/proto/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/proto/CMakeFiles/Caffe2_PROTO.dir
-- Up-to-date: /usr/local/./caffe2/proto/__init__.py
-- Up-to-date: /usr/local/./caffe2/proto/prof_dag_pb2.py
-- Up-to-date: /usr/local/./caffe2/proto/caffe2_pb2.py
-- Up-to-date: /usr/local/./caffe2/proto/caffe2_legacy_pb2.py
-- Up-to-date: /usr/local/./caffe2/proto/hsm_pb2.py
-- Up-to-date: /usr/local/./caffe2/proto/metanet_pb2.py
-- Up-to-date: /usr/local/./caffe2/proto/predictor_consts_pb2.py
-- Up-to-date: /usr/local/./caffe2/contrib
-- Up-to-date: /usr/local/./caffe2/contrib/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/contrib/gloo
-- Up-to-date: /usr/local/./caffe2/contrib/gloo/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/contrib/gloo/__init__.py
-- Up-to-date: /usr/local/./caffe2/contrib/gloo/gloo_test.py
-- Up-to-date: /usr/local/./caffe2/contrib/nccl
-- Up-to-date: /usr/local/./caffe2/contrib/nccl/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/contrib/nccl/__init__.py
-- Up-to-date: /usr/local/./caffe2/contrib/nccl/nccl_ops_test.py
-- Up-to-date: /usr/local/./caffe2/contrib/nnpack
-- Up-to-date: /usr/local/./caffe2/contrib/nnpack/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/contrib/nnpack/__init__.py
-- Up-to-date: /usr/local/./caffe2/contrib/nnpack/nnpack_ops_test.py
-- Up-to-date: /usr/local/./caffe2/contrib/observers
-- Up-to-date: /usr/local/./caffe2/contrib/observers/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/contrib/shm_mutex
-- Up-to-date: /usr/local/./caffe2/contrib/shm_mutex/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/contrib/__init__.py
-- Up-to-date: /usr/local/./caffe2/contrib/prof
-- Up-to-date: /usr/local/./caffe2/contrib/prof/__init__.py
-- Up-to-date: /usr/local/./caffe2/contrib/prof/cuda_profile_ops_test.py
-- Up-to-date: /usr/local/./caffe2/contrib/prof/htrace_to_chrome.py
-- Up-to-date: /usr/local/./caffe2/contrib/torch
-- Up-to-date: /usr/local/./caffe2/contrib/torch/__init__.py
-- Up-to-date: /usr/local/./caffe2/contrib/torch/th_ops_test.py
-- Up-to-date: /usr/local/./caffe2/contrib/torch/torch_ops_test.py
-- Up-to-date: /usr/local/./caffe2/contrib/warpctc
-- Up-to-date: /usr/local/./caffe2/contrib/warpctc/__init__.py
-- Up-to-date: /usr/local/./caffe2/contrib/warpctc/ctc_ops_test.py
-- Up-to-date: /usr/local/./caffe2/core
-- Up-to-date: /usr/local/./caffe2/core/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/cuda_rtc
-- Up-to-date: /usr/local/./caffe2/cuda_rtc/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/db
-- Up-to-date: /usr/local/./caffe2/db/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/distributed
-- Up-to-date: /usr/local/./caffe2/distributed/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/distributed/__init__.py
-- Up-to-date: /usr/local/./caffe2/distributed/file_store_handler_op_test.py
-- Up-to-date: /usr/local/./caffe2/distributed/redis_store_handler_op_test.py
-- Up-to-date: /usr/local/./caffe2/distributed/store_ops_test_util.py
-- Up-to-date: /usr/local/./caffe2/image
-- Up-to-date: /usr/local/./caffe2/image/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/video
-- Up-to-date: /usr/local/./caffe2/video/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/mkl
-- Up-to-date: /usr/local/./caffe2/mkl/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/mobile
-- Up-to-date: /usr/local/./caffe2/mobile/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/mobile/contrib
-- Up-to-date: /usr/local/./caffe2/mobile/contrib/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/mobile/contrib/ios
-- Up-to-date: /usr/local/./caffe2/mobile/contrib/ios/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/mobile/contrib/opengl
-- Up-to-date: /usr/local/./caffe2/mobile/contrib/opengl/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/mpi
-- Up-to-date: /usr/local/./caffe2/mpi/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/operators
-- Up-to-date: /usr/local/./caffe2/operators/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/perfkernels
-- Up-to-date: /usr/local/./caffe2/perfkernels/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/perfkernels/CMakeFiles/Caffe2_perfkernels_avx2.dir
-- Up-to-date: /usr/local/./caffe2/perfkernels/CMakeFiles/Caffe2_perfkernels_avx.dir
-- Up-to-date: /usr/local/./caffe2/perfkernels/__init__.py
-- Up-to-date: /usr/local/./caffe2/perfkernels/hp_emblookup_codegen.py
-- Up-to-date: /usr/local/./caffe2/python
-- Up-to-date: /usr/local/./caffe2/python/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/python/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/docs
-- Up-to-date: /usr/local/./caffe2/python/docs/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/docs/formatter.py
-- Up-to-date: /usr/local/./caffe2/python/docs/generator.py
-- Up-to-date: /usr/local/./caffe2/python/docs/github.py
-- Up-to-date: /usr/local/./caffe2/python/docs/parser.py
-- Up-to-date: /usr/local/./caffe2/python/examples
-- Up-to-date: /usr/local/./caffe2/python/examples/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/examples/char_rnn.py
-- Up-to-date: /usr/local/./caffe2/python/examples/lmdb_create_example.py
-- Up-to-date: /usr/local/./caffe2/python/examples/resnet50_trainer.py
-- Up-to-date: /usr/local/./caffe2/python/helpers
-- Up-to-date: /usr/local/./caffe2/python/helpers/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/helpers/algebra.py
-- Up-to-date: /usr/local/./caffe2/python/helpers/arg_scope.py
-- Up-to-date: /usr/local/./caffe2/python/helpers/array_helpers.py
-- Up-to-date: /usr/local/./caffe2/python/helpers/conv.py
-- Up-to-date: /usr/local/./caffe2/python/helpers/dropout.py
-- Up-to-date: /usr/local/./caffe2/python/helpers/elementwise_linear.py
-- Up-to-date: /usr/local/./caffe2/python/helpers/fc.py
-- Up-to-date: /usr/local/./caffe2/python/helpers/nonlinearity.py
-- Up-to-date: /usr/local/./caffe2/python/helpers/normalization.py
-- Up-to-date: /usr/local/./caffe2/python/helpers/pooling.py
-- Up-to-date: /usr/local/./caffe2/python/helpers/tools.py
-- Up-to-date: /usr/local/./caffe2/python/helpers/train.py
-- Up-to-date: /usr/local/./caffe2/python/layers
-- Up-to-date: /usr/local/./caffe2/python/layers/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/layers/add_bias.py
-- Up-to-date: /usr/local/./caffe2/python/layers/arc_cosine_feature_map.py
-- Up-to-date: /usr/local/./caffe2/python/layers/batch_distill_lr_loss.py
-- Up-to-date: /usr/local/./caffe2/python/layers/batch_lr_loss.py
-- Up-to-date: /usr/local/./caffe2/python/layers/batch_mse_loss.py
-- Up-to-date: /usr/local/./caffe2/python/layers/batch_normalization.py
-- Up-to-date: /usr/local/./caffe2/python/layers/batch_sigmoid_cross_entropy_loss.py
-- Up-to-date: /usr/local/./caffe2/python/layers/batch_softmax_loss.py
-- Up-to-date: /usr/local/./caffe2/python/layers/build_index.py
-- Up-to-date: /usr/local/./caffe2/python/layers/concat.py
-- Up-to-date: /usr/local/./caffe2/python/layers/conv.py
-- Up-to-date: /usr/local/./caffe2/python/layers/dropout.py
-- Up-to-date: /usr/local/./caffe2/python/layers/fc.py
-- Up-to-date: /usr/local/./caffe2/python/layers/fc_without_bias.py
-- Up-to-date: /usr/local/./caffe2/python/layers/feature_sparse_to_dense.py
-- Up-to-date: /usr/local/./caffe2/python/layers/functional.py
-- Up-to-date: /usr/local/./caffe2/python/layers/gather_record.py
-- Up-to-date: /usr/local/./caffe2/python/layers/last_n_window_collector.py
-- Up-to-date: /usr/local/./caffe2/python/layers/layers.py
-- Up-to-date: /usr/local/./caffe2/python/layers/merge_id_lists.py
-- Up-to-date: /usr/local/./caffe2/python/layers/pairwise_dot_product.py
-- Up-to-date: /usr/local/./caffe2/python/layers/position_weighted.py
-- Up-to-date: /usr/local/./caffe2/python/layers/random_fourier_features.py
-- Up-to-date: /usr/local/./caffe2/python/layers/reservoir_sampling.py
-- Up-to-date: /usr/local/./caffe2/python/layers/sampling_train.py
-- Up-to-date: /usr/local/./caffe2/python/layers/sampling_trainable_mixin.py
-- Up-to-date: /usr/local/./caffe2/python/layers/select_record_by_context.py
-- Up-to-date: /usr/local/./caffe2/python/layers/semi_random_features.py
-- Up-to-date: /usr/local/./caffe2/python/layers/sparse_feature_hash.py
-- Up-to-date: /usr/local/./caffe2/python/layers/sparse_lookup.py
-- Up-to-date: /usr/local/./caffe2/python/layers/split.py
-- Up-to-date: /usr/local/./caffe2/python/layers/tags.py
-- Up-to-date: /usr/local/./caffe2/python/layers/uniform_sampling.py
-- Up-to-date: /usr/local/./caffe2/python/mint
-- Up-to-date: /usr/local/./caffe2/python/mint/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/mint/app.py
-- Up-to-date: /usr/local/./caffe2/python/mkl
-- Up-to-date: /usr/local/./caffe2/python/mkl/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/convnet_benchmarks.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_LRN_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_LRN_speed_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_conv_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_copy_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_elementwise_sum_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_fc_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_fc_speed_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_fill_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_pool_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_pool_speed_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_relu_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_sbn_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_sbn_speed_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/mkl_speed_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/rewrite_graph.py
-- Up-to-date: /usr/local/./caffe2/python/mkl/rewrite_graph_test.py
-- Up-to-date: /usr/local/./caffe2/python/modeling
-- Up-to-date: /usr/local/./caffe2/python/modeling/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/modeling/initializers.py
-- Up-to-date: /usr/local/./caffe2/python/modeling/initializers_test.py
-- Up-to-date: /usr/local/./caffe2/python/modeling/parameter_info.py
-- Up-to-date: /usr/local/./caffe2/python/modeling/parameter_sharing.py
-- Up-to-date: /usr/local/./caffe2/python/modeling/parameter_sharing_test.py
-- Up-to-date: /usr/local/./caffe2/python/models
-- Up-to-date: /usr/local/./caffe2/python/models/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/models/seq2seq
-- Up-to-date: /usr/local/./caffe2/python/models/seq2seq/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/models/seq2seq/beam_search.py
-- Up-to-date: /usr/local/./caffe2/python/models/seq2seq/seq2seq_beam_search_test.py
-- Up-to-date: /usr/local/./caffe2/python/models/seq2seq/seq2seq_model_helper.py
-- Up-to-date: /usr/local/./caffe2/python/models/seq2seq/seq2seq_model_helper_test.py
-- Up-to-date: /usr/local/./caffe2/python/models/seq2seq/seq2seq_util.py
-- Up-to-date: /usr/local/./caffe2/python/models/seq2seq/train.py
-- Up-to-date: /usr/local/./caffe2/python/models/seq2seq/translate.py
-- Up-to-date: /usr/local/./caffe2/python/models/__sym_init__.py
-- Up-to-date: /usr/local/./caffe2/python/models/download.py
-- Up-to-date: /usr/local/./caffe2/python/models/resnet.py
-- Up-to-date: /usr/local/./caffe2/python/models/resnet_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test
-- Up-to-date: /usr/local/./caffe2/python/operator_test/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/activation_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/adagrad_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/adam_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/apmeter_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/atomic_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/batch_box_cox_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/blobs_queue_db_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/boolean_mask_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/boolean_unmask_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/channel_shuffle_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/checkpoint_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/clip_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/concat_split_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/conditional_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/conv_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/conv_transpose_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/copy_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/cosine_embedding_criterion_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/counter_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/crf_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/cross_entropy_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/cudnn_recurrent_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/dataset_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/distance_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/dropout_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/duplicate_operands_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/elementwise_linear_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/elementwise_logical_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/elementwise_op_broadcast_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/elementwise_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/emptysample_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/extend_tensor_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/fc_operator_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/filler_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/find_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/gather_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/gather_ranges_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/given_tensor_fill_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/group_conv_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/gru_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/hsm_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/im2col_col2im_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/image_input_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/index_hash_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/index_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/instance_norm_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/layer_norm_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/leaky_relu_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/lengths_tile_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/lengths_top_k_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/loss_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/lpnorm_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/map_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/margin_ranking_criterion_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/matmul_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/merge_id_lists_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/mkl_conv_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/mkl_packed_fc_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/mkl_speed_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/momentum_sgd_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/mpi_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/normalize_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/one_hot_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/pack_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/pack_rnn_sequence_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/pad_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/partition_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/piecewise_linear_transform_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/pooling_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/pow_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/prepend_dim_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/python_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/rank_loss_operator_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/rebatching_queue_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/record_queue_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/recurrent_net_executor_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/recurrent_network_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/reduce_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/reduction_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/relu_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/reshape_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/resize_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/rnn_cell_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/segment_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/sequence_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/shape_inference_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/sinusoid_position_encoding_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/softmax_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/softplus_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/sparse_gradient_checker_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/sparse_lengths_sum_benchmark.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/sparse_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/sparse_to_dense_mask_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/spatial_bn_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/specialized_segment_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/square_root_divide_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/stats_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/string_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/text_file_reader_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/tile_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/top_k_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/unique_uniform_fill_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/utility_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/operator_test/video_input_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/predictor
-- Up-to-date: /usr/local/./caffe2/python/predictor/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/predictor/mobile_exporter.py
-- Up-to-date: /usr/local/./caffe2/python/predictor/mobile_exporter_test.py
-- Up-to-date: /usr/local/./caffe2/python/predictor/predictor_exporter.py
-- Up-to-date: /usr/local/./caffe2/python/predictor/predictor_exporter_test.py
-- Up-to-date: /usr/local/./caffe2/python/predictor/predictor_py_utils.py
-- Up-to-date: /usr/local/./caffe2/python/predictor/serde.py
-- Up-to-date: /usr/local/./caffe2/python/rnn
-- Up-to-date: /usr/local/./caffe2/python/rnn/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/rnn/lstm_comparison.py
-- Up-to-date: /usr/local/./caffe2/python/rnn/rnn_cell_test_util.py
-- Up-to-date: /usr/local/./caffe2/python/tutorials
-- Up-to-date: /usr/local/./caffe2/python/tutorials/__init__.py
-- Up-to-date: /usr/local/./caffe2/python/tutorials/helpers.py
-- Up-to-date: /usr/local/./caffe2/python/test_util.py
-- Up-to-date: /usr/local/./caffe2/python/text_file_reader.py
-- Up-to-date: /usr/local/./caffe2/python/_import_c_extension.py
-- Up-to-date: /usr/local/./caffe2/python/allcompare_test.py
-- Up-to-date: /usr/local/./caffe2/python/attention.py
-- Up-to-date: /usr/local/./caffe2/python/benchmark_generator.py
-- Up-to-date: /usr/local/./caffe2/python/binarysize.py
-- Up-to-date: /usr/local/./caffe2/python/brew.py
-- Up-to-date: /usr/local/./caffe2/python/brew_test.py
-- Up-to-date: /usr/local/./caffe2/python/build.py
-- Up-to-date: /usr/local/./caffe2/python/caffe_translator.py
-- Up-to-date: /usr/local/./caffe2/python/caffe_translator_test.py
-- Up-to-date: /usr/local/./caffe2/python/checkpoint.py
-- Up-to-date: /usr/local/./caffe2/python/checkpoint_test.py
-- Up-to-date: /usr/local/./caffe2/python/cnn.py
-- Up-to-date: /usr/local/./caffe2/python/context.py
-- Up-to-date: /usr/local/./caffe2/python/context_test.py
-- Up-to-date: /usr/local/./caffe2/python/control.py
-- Up-to-date: /usr/local/./caffe2/python/control_ops_util.py
-- Up-to-date: /usr/local/./caffe2/python/control_test.py
-- Up-to-date: /usr/local/./caffe2/python/convnet_benchmarks.py
-- Up-to-date: /usr/local/./caffe2/python/convnet_benchmarks_test.py
-- Up-to-date: /usr/local/./caffe2/python/core.py
-- Up-to-date: /usr/local/./caffe2/python/core_gradients_test.py
-- Up-to-date: /usr/local/./caffe2/python/core_test.py
-- Up-to-date: /usr/local/./caffe2/python/crf.py
-- Up-to-date: /usr/local/./caffe2/python/data_parallel_model.py
-- Up-to-date: /usr/local/./caffe2/python/data_parallel_model_test.py
-- Up-to-date: /usr/local/./caffe2/python/data_workers.py
-- Up-to-date: /usr/local/./caffe2/python/data_workers_test.py
-- Up-to-date: /usr/local/./caffe2/python/dataio.py
-- Up-to-date: /usr/local/./caffe2/python/dataio_test.py
-- Up-to-date: /usr/local/./caffe2/python/dataset.py
-- Up-to-date: /usr/local/./caffe2/python/db_test.py
-- Up-to-date: /usr/local/./caffe2/python/device_checker.py
-- Up-to-date: /usr/local/./caffe2/python/dyndep.py
-- Up-to-date: /usr/local/./caffe2/python/embedding_generation_benchmark.py
-- Up-to-date: /usr/local/./caffe2/python/experiment_util.py
-- Up-to-date: /usr/local/./caffe2/python/extension_loader.py
-- Up-to-date: /usr/local/./caffe2/python/gradient_check_test.py
-- Up-to-date: /usr/local/./caffe2/python/gradient_checker.py
-- Up-to-date: /usr/local/./caffe2/python/gru_cell.py
-- Up-to-date: /usr/local/./caffe2/python/hsm_util.py
-- Up-to-date: /usr/local/./caffe2/python/hypothesis_test.py
-- Up-to-date: /usr/local/./caffe2/python/hypothesis_test_util.py
-- Up-to-date: /usr/local/./caffe2/python/layer_model_helper.py
-- Up-to-date: /usr/local/./caffe2/python/layer_model_instantiator.py
-- Up-to-date: /usr/local/./caffe2/python/layer_parameter_sharing_test.py
-- Up-to-date: /usr/local/./caffe2/python/layer_test_util.py
-- Up-to-date: /usr/local/./caffe2/python/layers_test.py
-- Up-to-date: /usr/local/./caffe2/python/lengths_reducer_rowwise_8bit_ops_test.py
-- Up-to-date: /usr/local/./caffe2/python/load_save_test.py
-- Up-to-date: /usr/local/./caffe2/python/lstm_benchmark.py
-- Up-to-date: /usr/local/./caffe2/python/memonger.py
-- Up-to-date: /usr/local/./caffe2/python/memonger_test.py
-- Up-to-date: /usr/local/./caffe2/python/mkl_test_util.py
-- Up-to-date: /usr/local/./caffe2/python/model_device_test.py
-- Up-to-date: /usr/local/./caffe2/python/model_helper.py
-- Up-to-date: /usr/local/./caffe2/python/muji.py
-- Up-to-date: /usr/local/./caffe2/python/muji_test.py
-- Up-to-date: /usr/local/./caffe2/python/net_builder.py
-- Up-to-date: /usr/local/./caffe2/python/net_builder_test.py
-- Up-to-date: /usr/local/./caffe2/python/net_drawer.py
-- Up-to-date: /usr/local/./caffe2/python/net_printer.py
-- Up-to-date: /usr/local/./caffe2/python/net_printer_test.py
-- Up-to-date: /usr/local/./caffe2/python/optimizer.py
-- Up-to-date: /usr/local/./caffe2/python/optimizer_context.py
-- Up-to-date: /usr/local/./caffe2/python/optimizer_test.py
-- Up-to-date: /usr/local/./caffe2/python/optimizer_test_util.py
-- Up-to-date: /usr/local/./caffe2/python/parallel_workers.py
-- Up-to-date: /usr/local/./caffe2/python/parallel_workers_test.py
-- Up-to-date: /usr/local/./caffe2/python/parallelize_gpu_bmuf_distributed_test.py
-- Up-to-date: /usr/local/./caffe2/python/pipeline.py
-- Up-to-date: /usr/local/./caffe2/python/pipeline_test.py
-- Up-to-date: /usr/local/./caffe2/python/predictor_constants.py
-- Up-to-date: /usr/local/./caffe2/python/python_op_test.py
-- Up-to-date: /usr/local/./caffe2/python/queue_util.py
-- Up-to-date: /usr/local/./caffe2/python/record_queue.py
-- Up-to-date: /usr/local/./caffe2/python/recurrent.py
-- Up-to-date: /usr/local/./caffe2/python/rnn_cell.py
-- Up-to-date: /usr/local/./caffe2/python/schema.py
-- Up-to-date: /usr/local/./caffe2/python/schema_test.py
-- Up-to-date: /usr/local/./caffe2/python/scope.py
-- Up-to-date: /usr/local/./caffe2/python/scope_test.py
-- Up-to-date: /usr/local/./caffe2/python/session.py
-- Up-to-date: /usr/local/./caffe2/python/session_test.py
-- Up-to-date: /usr/local/./caffe2/python/sparse_to_dense_mask_test.py
-- Up-to-date: /usr/local/./caffe2/python/task.py
-- Up-to-date: /usr/local/./caffe2/python/timeout_guard.py
-- Up-to-date: /usr/local/./caffe2/python/toy_regression_test.py
-- Up-to-date: /usr/local/./caffe2/python/tt_core.py
-- Up-to-date: /usr/local/./caffe2/python/tt_core_test.py
-- Up-to-date: /usr/local/./caffe2/python/utils.py
-- Up-to-date: /usr/local/./caffe2/python/visualize.py
-- Up-to-date: /usr/local/./caffe2/python/workspace.py
-- Up-to-date: /usr/local/./caffe2/python/workspace_test.py
-- Up-to-date: /usr/local/./caffe2/queue
-- Up-to-date: /usr/local/./caffe2/queue/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/sgd
-- Up-to-date: /usr/local/./caffe2/sgd/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/transforms
-- Up-to-date: /usr/local/./caffe2/transforms/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/utils
-- Up-to-date: /usr/local/./caffe2/utils/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/__init__.py
-- Up-to-date: /usr/local/./caffe2/experiments
-- Up-to-date: /usr/local/./caffe2/experiments/__init__.py
-- Up-to-date: /usr/local/./caffe2/experiments/python
-- Up-to-date: /usr/local/./caffe2/experiments/python/__init__.py
-- Up-to-date: /usr/local/./caffe2/experiments/python/SparseTransformer.py
-- Up-to-date: /usr/local/./caffe2/experiments/python/convnet_benchmarks.py
-- Up-to-date: /usr/local/./caffe2/experiments/python/device_reduce_sum_bench.py
-- Up-to-date: /usr/local/./caffe2/experiments/python/funhash_op_test.py
-- Up-to-date: /usr/local/./caffe2/experiments/python/net_construct_bench.py
-- Up-to-date: /usr/local/./caffe2/experiments/python/sparse_funhash_op_test.py
-- Up-to-date: /usr/local/./caffe2/experiments/python/sparse_reshape_op_test.py
-- Up-to-date: /usr/local/./caffe2/experiments/python/tt_contraction_op_test.py
-- Up-to-date: /usr/local/./caffe2/experiments/python/tt_pad_op_test.py
-- Up-to-date: /usr/local/./caffe2/binaries
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/tutorial_blob.dir
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/print_core_object_sizes.dir
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/inspect_gpus.dir
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/predictor_verifier.dir
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/convert_db.dir
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/print_registered_core_operators.dir
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/convert_caffe_image_db.dir
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/db_throughput.dir
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/run_plan.dir
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/make_mnist_db.dir
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/speed_benchmark.dir
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/make_cifar_db.dir
-- Up-to-date: /usr/local/./caffe2/binaries/CMakeFiles/split_db.dir
-- Up-to-date: /usr/local/./caffe2/binaries/binaries
-- Installing: /usr/local/include/caffe2/proto/caffe2.pb.h
-- Installing: /usr/local/include/caffe2/proto/caffe2_legacy.pb.h
-- Installing: /usr/local/include/caffe2/proto/hsm.pb.h
-- Installing: /usr/local/include/caffe2/proto/metanet.pb.h
-- Installing: /usr/local/include/caffe2/proto/predictor_consts.pb.h
-- Installing: /usr/local/include/caffe2/proto/prof_dag.pb.h
-- Installing: /usr/local/bin/convert_caffe_image_db
-- Set runtime path of "/usr/local/bin/convert_caffe_image_db" to ""
-- Installing: /usr/local/bin/convert_db
-- Set runtime path of "/usr/local/bin/convert_db" to ""
-- Installing: /usr/local/bin/db_throughput
-- Set runtime path of "/usr/local/bin/db_throughput" to ""
-- Installing: /usr/local/bin/make_cifar_db
-- Set runtime path of "/usr/local/bin/make_cifar_db" to ""
-- Installing: /usr/local/bin/make_mnist_db
-- Set runtime path of "/usr/local/bin/make_mnist_db" to ""
-- Installing: /usr/local/bin/predictor_verifier
-- Set runtime path of "/usr/local/bin/predictor_verifier" to ""
-- Installing: /usr/local/bin/print_registered_core_operators
-- Set runtime path of "/usr/local/bin/print_registered_core_operators" to ""
-- Installing: /usr/local/bin/run_plan
-- Set runtime path of "/usr/local/bin/run_plan" to ""
-- Installing: /usr/local/bin/speed_benchmark
-- Set runtime path of "/usr/local/bin/speed_benchmark" to ""
-- Installing: /usr/local/bin/split_db
-- Set runtime path of "/usr/local/bin/split_db" to ""
-- Installing: /usr/local/bin/inspect_gpus
-- Set runtime path of "/usr/local/bin/inspect_gpus" to ""
-- Installing: /usr/local/bin/print_core_object_sizes
-- Set runtime path of "/usr/local/bin/print_core_object_sizes" to ""
-- Installing: /usr/local/bin/tutorial_blob
-- Set runtime path of "/usr/local/bin/tutorial_blob" to ""


```

* add the following lines in your ~/.bashrc file

```sh

# for caffe2
export PYTHONPATH=/usr/local${PYTHONPATH:+:${PYTHONPATH}}
export PYTHONPATH=/caffe2/build:$PYTHONPATH
export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH

```

## Run test

```sh

python2 -c 'from caffe2.python import core' 2>/dev/null && echo "Success" || echo "Failure"
python2 -m caffe2.python.operator_test.relu_op_test

```