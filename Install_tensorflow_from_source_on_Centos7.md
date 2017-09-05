# install python3 with miniconda on Centos 7

## system: fully installed Centos 7
* system update

## Install bazel
* Download bazel from https://github.com/bazelbuild/bazel/releases

* Install bazel as root
```sh
$ sudo sh bazel-0.5.4-installer-linux-x86_64.sh

Bazel installer
---------------

Bazel is bundled with software licensed under the GPLv2 with Classpath exception.
You can find the sources next to the installer on our release page:
   https://github.com/bazelbuild/bazel/releases

# Release 0.5.4 (2017-08-25)

Baseline: 6563b2d42d29196432d5fcafa0144b8371fbb028

Cherry picks:
   + d4fa181f8607c35230b7efa1ce94188b51508962:
     Use getExecPathString when getting bash_main_file
   + 837e1b3d4859140d29aaa6bbab8fbb008e6d701e:
     Windows, sh_bin. launcher: export runfiles envvars
   + fe9ba893c0ebec19228086356af5fa8d81f2809b:
     grpc: Consolidate gRPC code from BES and Remote Execution. Fixes
     #3460, #3486
   + e8d4366cd374fba92f1425de0d475411c8defda4:
     Automated rollback of commit
     496d3ded0bce12b7371a93e1183ba30e6aa88032.
   + 242a43449dd44a22857f6ce95f7cc6a7e134d298:
     bes,remote: update default auth scope.
   + 793b409eeae2b42be7fed58251afa87b5733ca4d:
     Windows, sh_bin. launcher: fix manifest path
   + 7e4fbbe4ab3915a57b2187408c3909e5cd6c6013:
     Add --windows_exe_launcher option
   + 91fb38e92ace6cf14ce5da6527d71320b4e3f3d2:
     remote_worker: Serialize fork() calls. Fixes #3356
   + b79a9fcd40f448d3aebb2b93a2ebe80d09b38408:
     Quote python_path and launcher in
     python_stub_template_windows.txt
   + 4a2e17f85fc8450aa084b201c5f24b30010c5987:
     Add build_windows_jni.sh back
   + ce61d638197251f71ed90db74843b55d9c2e9ae5:
     don't use methods and classes removed in upstream dx RELNOTES:
     update dexing tools to Android SDK 26.0.1
   + 5393a4996d701fa192964a35cbb75e558a0599c0:
     Make Bazel enforce requirement on build-tools 26.0.1 or later.
   + 5fac03570f80856c063c6019f5beb3bdc1672dee:
     Fix --verbose_failures w/ sandboxing to print the full command
     line
   + f7bd1acf1f96bb7e3e19edb9483d9e07eb5af070:
     Only patch in C++ compile features when they are not already
     defined in crosstool
   + d7f5c120417bc2d2344dfb285322355f225d9153:
     Bump python-gflags to 3.1.0, take two
   + 3cb136d5451e9d8af58f9a99990cad0592df101a:
     Add python to bazel's dockerfiles

New features:

  - Do not disable fully dynamic linking with ThinLTO when invoked
    via LIPO options.

Important changes:

  - Ignore --glibc in the Android transition.
  - Remove --experimental_android_use_singlejar_for_multidex.
  - nocopts now also filter copts
  - The Build Event Service (BES) client now properly supports
    Google Applicaton Default Credentials.
  - update dexing tools to Android SDK 26.0.1
  - Bazel Android support now requires build-tools 26.0.1 or later.
  - Fix a bug in the remote_worker that would at times make it crash on Linux. See #3356
  - The java_proto_library rule now supports generated sources. See #2265

## Build informations
   - [Commit](https://github.com/bazelbuild/bazel/commit/67f23f5)
Uncompressing.......

Bazel is now installed!

Make sure you have "/usr/local/bin" in your path. You can also activate bash
completion by adding the following line to your ~/.bashrc:
  source /usr/local/lib/bazel/bin/bazel-complete.bash

See http://bazel.build/docs/getting-started.html to start a new project!


```

## install python dependences
```sh
sudo /miniconda3/bin/pip install six numpy wheel 

```

## compile and build tensorflow
* download
```sh
$ wget https://github.com/tensorflow/tensorflow/archive/v1.3.0.tar.gz
$ tar zxf v1.3.0.tar.gz
$ cd tensorflow-1.3.0
```

* configure
```sh
$ ./configure 
You have bazel 0.5.4 installed.
Please specify the location of python. [Default is /miniconda3/bin/python]: 
Found possible Python library paths:
  /miniconda3/lib/python3.6/site-packages
Please input the desired Python library path to use.  Default is [/miniconda3/lib/python3.6/site-packages]

Using python library path: /miniconda3/lib/python3.6/site-packages
Do you wish to build TensorFlow with MKL support? [y/N] 
No MKL support will be enabled for TensorFlow
Please specify optimization flags to use during compilation when bazel option "--config=opt" is specified [Default is -march=native]: 
Do you wish to use jemalloc as the malloc implementation? [Y/n] 
jemalloc enabled
Do you wish to build TensorFlow with Google Cloud Platform support? [y/N] 
No Google Cloud Platform support will be enabled for TensorFlow
Do you wish to build TensorFlow with Hadoop File System support? [y/N] 
No Hadoop File System support will be enabled for TensorFlow
Do you wish to build TensorFlow with the XLA just-in-time compiler (experimental)? [y/N] 
No XLA support will be enabled for TensorFlow
Do you wish to build TensorFlow with VERBS support? [y/N] 
No VERBS support will be enabled for TensorFlow
Do you wish to build TensorFlow with OpenCL support? [y/N] 
No OpenCL support will be enabled for TensorFlow
Do you wish to build TensorFlow with CUDA support? [y/N] Y
CUDA support will be enabled for TensorFlow
Do you want to use clang as CUDA compiler? [y/N] 
nvcc will be used as CUDA compiler
Please specify the CUDA SDK version you want to use, e.g. 7.0. [Leave empty to default to CUDA 8.0]: 
Please specify the location where CUDA 8.0 toolkit is installed. Refer to README.md for more details. [Default is /usr/local/cuda]: 
Please specify which gcc should be used by nvcc as the host compiler. [Default is /usr/bin/gcc]: 
Please specify the cuDNN version you want to use. [Leave empty to default to cuDNN 6.0]: 
Please specify the location where cuDNN 6 library is installed. Refer to README.md for more details. [Default is /usr/local/cuda]: 
Please specify a list of comma-separated Cuda compute capabilities you want to build with.
You can find the compute capability of your device at: https://developer.nvidia.com/cuda-gpus.
Please note that each additional compute capability significantly increases your build time and binary size.
[Default is: "6.1,6.1"]: 
Do you wish to build TensorFlow with MPI support? [y/N] 
MPI support will not be enabled for TensorFlow
Configuration finished
```

## build 
```sh
$ bazel build --config=opt --copt=-mavx --copt=-mavx2 --copt=-mfma --copt=-mfpmath=both --copt=-msse4.2 --config=cuda //tensorflow/tools/pip_package:build_pip_package 
...
...
...
Target //tensorflow/tools/pip_package:build_pip_package up-to-date:
  bazel-bin/tensorflow/tools/pip_package/build_pip_package
INFO: Elapsed time: 609.642s, Critical Path: 183.94s

$  bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg
Tue Sep 5 15:57:13 CST 2017 : === Using tmpdir: /tmp/tmp.JRSELc04L4
~/gpuServer/tensorflow-1.3.0/bazel-bin/tensorflow/tools/pip_package/build_pip_package.runfiles ~/gpuServer/tensorflow-1.3.0
~/gpuServer/tensorflow-1.3.0
/tmp/tmp.JRSELc04L4 ~/gpuServer/tensorflow-1.3.0
Tue Sep 5 15:57:15 CST 2017 : === Building wheel
warning: no files found matching '*.dll' under directory '*'
warning: no files found matching '*.lib' under directory '*'
warning: no files found matching '*.h' under directory 'tensorflow/include/tensorflow'
warning: no files found matching '*' under directory 'tensorflow/include/Eigen'
warning: no files found matching '*' under directory 'tensorflow/include/external'
warning: no files found matching '*.h' under directory 'tensorflow/include/google'
warning: no files found matching '*' under directory 'tensorflow/include/third_party'
warning: no files found matching '*' under directory 'tensorflow/include/unsupported'
~/gpuServer/tensorflow-1.3.0
Tue Sep 5 15:57:33 CST 2017 : === Output wheel file is in: /tmp/tensorflow_pkg

$ sudo /miniconda3/bin/pip install /tmp/tensorflow_pkg/tensorflow-1.3.0-cp36-cp36m-linux_x86_64.whl 
Processing /tmp/tensorflow_pkg/tensorflow-1.3.0-cp36-cp36m-linux_x86_64.whl
Collecting protobuf>=3.3.0 (from tensorflow==1.3.0)
  Downloading protobuf-3.4.0-cp36-cp36m-manylinux1_x86_64.whl (6.2MB)
    100% |████████████████████████████████| 6.2MB 144kB/s 
Collecting tensorflow-tensorboard<0.2.0,>=0.1.0 (from tensorflow==1.3.0)
  Downloading tensorflow_tensorboard-0.1.5-py3-none-any.whl (2.2MB)
    100% |████████████████████████████████| 2.2MB 389kB/s 
Requirement already satisfied: wheel>=0.26 in /miniconda3/lib/python3.6/site-packages (from tensorflow==1.3.0)
Requirement already satisfied: six>=1.10.0 in /miniconda3/lib/python3.6/site-packages (from tensorflow==1.3.0)
Requirement already satisfied: numpy>=1.11.0 in /miniconda3/lib/python3.6/site-packages (from tensorflow==1.3.0)
Requirement already satisfied: setuptools in /miniconda3/lib/python3.6/site-packages/setuptools-27.2.0-py3.6.egg (from protobuf>=3.3.0->tensorflow==1.3.0)
Collecting html5lib==0.9999999 (from tensorflow-tensorboard<0.2.0,>=0.1.0->tensorflow==1.3.0)
  Using cached html5lib-0.9999999.tar.gz
Collecting bleach==1.5.0 (from tensorflow-tensorboard<0.2.0,>=0.1.0->tensorflow==1.3.0)
  Using cached bleach-1.5.0-py2.py3-none-any.whl
Collecting werkzeug>=0.11.10 (from tensorflow-tensorboard<0.2.0,>=0.1.0->tensorflow==1.3.0)
  Using cached Werkzeug-0.12.2-py2.py3-none-any.whl
Collecting markdown>=2.6.8 (from tensorflow-tensorboard<0.2.0,>=0.1.0->tensorflow==1.3.0)
  Using cached Markdown-2.6.9.tar.gz
Building wheels for collected packages: html5lib, markdown
  Running setup.py bdist_wheel for html5lib ... done
  Stored in directory: /root/.cache/pip/wheels/6f/85/6c/56b8e1292c6214c4eb73b9dda50f53e8e977bf65989373c962
  Running setup.py bdist_wheel for markdown ... done
  Stored in directory: /root/.cache/pip/wheels/bf/46/10/c93e17ae86ae3b3a919c7b39dad3b5ccf09aeb066419e5c1e5
Successfully built html5lib markdown
Installing collected packages: protobuf, html5lib, bleach, werkzeug, markdown, tensorflow-tensorboard, tensorflow
Successfully installed bleach-1.5.0 html5lib-0.9999999 markdown-2.6.9 protobuf-3.4.0 tensorflow-1.3.0 tensorflow-tensorboard-0.1.5 werkzeug-0.12.2
```

## install ipython and run test
```sh
sudo /miniconda3/bin/pip install ipython
```

```sh
$ cd
$ ipython
Python 3.6.1 |Continuum Analytics, Inc.| (default, May 11 2017, 13:09:58) 
Type 'copyright', 'credits' or 'license' for more information
IPython 6.1.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: import tensorflow as tf

In [2]: sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))
2017-09-05 16:04:26.039791: I tensorflow/core/common_runtime/gpu/gpu_device.cc:955] Found device 0 with properties: 
name: GeForce GTX 1080 Ti
major: 6 minor: 1 memoryClockRate (GHz) 1.62
pciBusID 0000:04:00.0
Total memory: 10.91GiB
Free memory: 10.75GiB
2017-09-05 16:04:26.349443: W tensorflow/stream_executor/cuda/cuda_driver.cc:523] A non-primary context 0x2f52b10 exists before initializing the StreamExecutor. We haven't verified StreamExecutor works with that.
2017-09-05 16:04:26.350289: I tensorflow/core/common_runtime/gpu/gpu_device.cc:955] Found device 1 with properties: 
name: GeForce GTX 1080 Ti
major: 6 minor: 1 memoryClockRate (GHz) 1.62
pciBusID 0000:81:00.0
Total memory: 10.91GiB
Free memory: 10.75GiB
2017-09-05 16:04:26.350395: I tensorflow/core/common_runtime/gpu/gpu_device.cc:847] Peer access not supported between device ordinals 0 and 1
2017-09-05 16:04:26.350418: I tensorflow/core/common_runtime/gpu/gpu_device.cc:847] Peer access not supported between device ordinals 1 and 0
2017-09-05 16:04:26.350454: I tensorflow/core/common_runtime/gpu/gpu_device.cc:976] DMA: 0 1 
2017-09-05 16:04:26.350468: I tensorflow/core/common_runtime/gpu/gpu_device.cc:986] 0:   Y N 
2017-09-05 16:04:26.350483: I tensorflow/core/common_runtime/gpu/gpu_device.cc:986] 1:   N Y 
2017-09-05 16:04:26.350504: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1045] Creating TensorFlow device (/gpu:0) -> (device: 0, name: GeForce GTX 1080 Ti, pci bus id: 0000:04:00.0)
2017-09-05 16:04:26.350518: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1045] Creating TensorFlow device (/gpu:1) -> (device: 1, name: GeForce GTX 1080 Ti, pci bus id: 0000:81:00.0)
Device mapping:
/job:localhost/replica:0/task:0/gpu:0 -> device: 0, name: GeForce GTX 1080 Ti, pci bus id: 0000:04:00.0
/job:localhost/replica:0/task:0/gpu:1 -> device: 1, name: GeForce GTX 1080 Ti, pci bus id: 0000:81:00.0
2017-09-05 16:04:26.563322: I tensorflow/core/common_runtime/direct_session.cc:300] Device mapping:
/job:localhost/replica:0/task:0/gpu:0 -> device: 0, name: GeForce GTX 1080 Ti, pci bus id: 0000:04:00.0
/job:localhost/replica:0/task:0/gpu:1 -> device: 1, name: GeForce GTX 1080 Ti, pci bus id: 0000:81:00.0
```