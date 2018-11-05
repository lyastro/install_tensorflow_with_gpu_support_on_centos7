```sh

$ ./configure
You have bazel 0.5.4 installed.
Please specify the location of python. [Default is /opt/anaconda/3/bin/python]:


Found possible Python library paths:
  /opt/anaconda/3/lib/python3.6/site-packages
Please input the desired Python library path to use.  Default is [/opt/anaconda/3/lib/python3.6/site-packages]

Do you wish to build TensorFlow with jemalloc as malloc support? [Y/n]:
jemalloc as malloc support will be enabled for TensorFlow.

Do you wish to build TensorFlow with Google Cloud Platform support? [Y/n]: n
No Google Cloud Platform support will be enabled for TensorFlow.

Do you wish to build TensorFlow with Hadoop File System support? [Y/n]: n
No Hadoop File System support will be enabled for TensorFlow.

Do you wish to build TensorFlow with Amazon S3 File System support? [Y/n]: n
No Amazon S3 File System support will be enabled for TensorFlow.

Do you wish to build TensorFlow with XLA JIT support? [y/N]:
No XLA JIT support will be enabled for TensorFlow.

Do you wish to build TensorFlow with GDR support? [y/N]:
No GDR support will be enabled for TensorFlow.

Do you wish to build TensorFlow with VERBS support? [y/N]:
No VERBS support will be enabled for TensorFlow.

Do you wish to build TensorFlow with OpenCL SYCL support? [y/N]:
No OpenCL SYCL support will be enabled for TensorFlow.

Do you wish to build TensorFlow with CUDA support? [y/N]: y
CUDA support will be enabled for TensorFlow.

Please specify the CUDA SDK version you want to use, e.g. 7.0. [Leave empty to default to CUDA 9.0]: 8.0


Please specify the location where CUDA 8.0 toolkit is installed. Refer to README.md for more details. [Default is /usr/local/cuda]:


Please specify the cuDNN version you want to use. [Leave empty to default to cuDNN 7.0]: 6.0


Please specify the location where cuDNN 6.0 library is installed. Refer to README.md for more details. [Default is /usr/local/cuda]:


Invalid path to cuDNN 6.0 toolkit. None of the following files can be found:
/usr/local/cuda-8.0/lib64/libcudnn.so.6.0
/usr/local/cuda-8.0/libcudnn.so.6.0
None.6.0
Please specify the cuDNN version you want to use. [Leave empty to default to cuDNN 7.0]: 6.0


Please specify the location where cuDNN 6.0 library is installed. Refer to README.md for more details. [Default is /usr/local/cuda]:


Invalid path to cuDNN 6.0 toolkit. None of the following files can be found:
/usr/local/cuda-8.0/lib64/libcudnn.so.6.0
/usr/local/cuda-8.0/libcudnn.so.6.0
None.6.0
Please specify the cuDNN version you want to use. [Leave empty to default to cuDNN 7.0]: cuDNN 6.0


Please specify the location where cuDNN cuDNN 6.0 library is installed. Refer to README.md for more details. [Default is /usr/local/cuda]:


Invalid path to cuDNN cuDNN 6.0 toolkit. None of the following files can be found:
/usr/local/cuda-8.0/lib64/libcudnn.so.cuDNN 6.0
/usr/local/cuda-8.0/libcudnn.so.cuDNN 6.0
None.cuDNN 6.0
Please specify the cuDNN version you want to use. [Leave empty to default to cuDNN 7.0]: 6.0


Please specify the location where cuDNN 6.0 library is installed. Refer to README.md for more details. [Default is /usr/local/cuda]:


Invalid path to cuDNN 6.0 toolkit. None of the following files can be found:
/usr/local/cuda-8.0/lib64/libcudnn.so.6.0
/usr/local/cuda-8.0/libcudnn.so.6.0
None.6.0
Please specify the cuDNN version you want to use. [Leave empty to default to cuDNN 7.0]: 6.1


Please specify the location where cuDNN 6.1 library is installed. Refer to README.md for more details. [Default is /usr/local/cuda]:


Invalid path to cuDNN 6.1 toolkit. None of the following files can be found:
/usr/local/cuda-8.0/lib64/libcudnn.so.6.1
/usr/local/cuda-8.0/libcudnn.so.6.1
None.6.1
Please specify the cuDNN version you want to use. [Leave empty to default to cuDNN 7.0]: 6


Please specify the location where cuDNN 6 library is installed. Refer to README.md for more details. [Default is /usr/local/cuda]:


Please specify a list of comma-separated Cuda compute capabilities you want to build with.
You can find the compute capability of your device at: https://developer.nvidia.com/cuda-gpus.
Please note that each additional compute capability significantly increases your build time and binary size. [Default is: 6.1,6.1]


Do you want to use clang as CUDA compiler? [y/N]:
nvcc will be used as CUDA compiler.

Please specify which gcc should be used by nvcc as the host compiler. [Default is /usr/bin/gcc]:


Do you wish to build TensorFlow with MPI support? [y/N]:
No MPI support will be enabled for TensorFlow.

Please specify optimization flags to use during compilation when bazel option "--config=opt" is specified [Default is -march=native]:


Add "--config=mkl" to your bazel command to build with MKL support.
Please note that MKL on MacOS or windows is still not supported.
If you would like to use a local MKL instead of downloading, please set the environment variable "TF_MKL_ROOT" every time before build.

Would you like to interactively configure ./WORKSPACE for Android builds? [y/N]:
Not configuring the WORKSPACE for Android builds.

Configuration finished
```

```sh
$ bazel build --config=opt --config=mkl --copt=-mavx --copt=-mavx2 --copt=-mfma --copt=-mfpmath=both --copt=-msse4.2 --config=cuda //tensorflow/tools/pip_package:build_pip_package
...........
Target //tensorflow/tools/pip_package:build_pip_package up-to-date:
  bazel-bin/tensorflow/tools/pip_package/build_pip_package
INFO: Elapsed time: 873.258s, Critical Path: 256.24s
```

```sh
$ bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg
Thu Jan 4 16:07:16 CST 2018 : === Using tmpdir: /tmp/tmp.8vscW43S7z
~/installCUDA/tensorflow/bazel-bin/tensorflow/tools/pip_package/build_pip_package.runfiles ~/installCUDA/tensorflow
~/installCUDA/tensorflow
/tmp/tmp.8vscW43S7z ~/installCUDA/tensorflow
Thu Jan 4 16:07:18 CST 2018 : === Building wheel
warning: no files found matching '*.dll' under directory '*'
warning: no files found matching '*.lib' under directory '*'
warning: no files found matching '*.h' under directory 'tensorflow/include/tensorflow'
warning: no files found matching '*' under directory 'tensorflow/include/Eigen'
warning: no files found matching '*' under directory 'tensorflow/include/external'
warning: no files found matching '*.h' under directory 'tensorflow/include/google'
warning: no files found matching '*' under directory 'tensorflow/include/third_party'
warning: no files found matching '*' under directory 'tensorflow/include/unsupported'
~/installCUDA/tensorflow
Thu Jan 4 16:07:43 CST 2018 : === Output wheel file is in: /tmp/tensorflow_pkg
```

```sh$ sudo /opt/anaconda/3/bin/pip install /tmp/tensorflow_pkg/tensorflow-1.4.0-cp36-cp36m-linux_x86_64.whl
Processing /tmp/tensorflow_pkg/tensorflow-1.4.0-cp36-cp36m-linux_x86_64.whl
Requirement already satisfied: numpy>=1.12.1 in /opt/anaconda/3/lib/python3.6/site-packages (from tensorflow==1.4.0)
Requirement already satisfied: tensorflow-tensorboard in /opt/anaconda/3/lib/python3.6/site-packages (from tensorflow==1.4.0)
Requirement already satisfied: protobuf>=3.4.0 in /opt/anaconda/3/lib/python3.6/site-packages (from tensorflow==1.4.0)
Collecting absl-py>=0.1.6 (from tensorflow==1.4.0)
  Downloading http://mirrors.aliyun.com/pypi/packages/3d/29/3365a36444e021dd8057aa08dc211f0c7d5d4894bac3d1b171e3dcb1748b/absl-py-0.1.7.tar.gz (78kB)
    100% |████████████████████████████████| 81kB 1.5MB/s
Requirement already satisfied: wheel>=0.26 in /opt/anaconda/3/lib/python3.6/site-packages (from tensorflow==1.4.0)
Collecting gast>=0.2.0 (from tensorflow==1.4.0)
  Downloading http://mirrors.aliyun.com/pypi/packages/5c/78/ff794fcae2ce8aa6323e789d1f8b3b7765f601e7702726f430e814822b96/gast-0.2.0.tar.gz
Requirement already satisfied: six>=1.10.0 in /opt/anaconda/3/lib/python3.6/site-packages (from tensorflow==1.4.0)
Requirement already satisfied: bleach==1.5.0 in /opt/anaconda/3/lib/python3.6/site-packages (from tensorflow-tensorboard->tensorflow==1.4.0)
Requirement already satisfied: werkzeug>=0.11.10 in /opt/anaconda/3/lib/python3.6/site-packages (from tensorflow-tensorboard->tensorflow==1.4.0)
Requirement already satisfied: markdown>=2.6.8 in /opt/anaconda/3/lib/python3.6/site-packages (from tensorflow-tensorboard->tensorflow==1.4.0)
Requirement already satisfied: html5lib==0.9999999 in /opt/anaconda/3/lib/python3.6/site-packages (from tensorflow-tensorboard->tensorflow==1.4.0)
Requirement already satisfied: setuptools in /opt/anaconda/3/lib/python3.6/site-packages (from protobuf>=3.4.0->tensorflow==1.4.0)
Building wheels for collected packages: absl-py, gast
  Running setup.py bdist_wheel for absl-py ... done
  Stored in directory: /root/.cache/pip/wheels/7d/65/3a/e1556d9a0ac7e77512b9b2249d8f534cdcb616f98c273bf058
  Running setup.py bdist_wheel for gast ... done
  Stored in directory: /root/.cache/pip/wheels/17/0a/dc/bb6d7b129029482a8d55901d66b65e756a681f6a1da7297a9b
Successfully built absl-py gast
Installing collected packages: absl-py, gast, tensorflow
Successfully installed absl-py-0.1.7 gast-0.2.0 tensorflow-1.4.0
```

```sh
$ cd
$ ipython
Python 3.6.3 |Anaconda custom (64-bit)| (default, Oct 13 2017, 12:02:49)
Type 'copyright', 'credits' or 'license' for more information
IPython 6.1.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: import tensorflow as tf

In [2]: hello = tf.constant('Hello, TensorFlow!')

In [3]: sess = tf.Session()
2018-01-04 16:12:40.569080: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1206] Found device 0 with properties:
name: GeForce GTX 1080 Ti major: 6 minor: 1 memoryClockRate(GHz): 1.62
pciBusID: 0000:02:00.0
totalMemory: 10.91GiB freeMemory: 10.75GiB
2018-01-04 16:12:40.887313: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1206] Found device 1 with properties:
name: GeForce GTX 1080 Ti major: 6 minor: 1 memoryClockRate(GHz): 1.62
pciBusID: 0000:03:00.0
totalMemory: 10.91GiB freeMemory: 10.75GiB
2018-01-04 16:12:40.888272: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1221] Device peer to peer matrix
2018-01-04 16:12:40.888324: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1227] DMA: 0 1
2018-01-04 16:12:40.888342: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1237] 0:   Y Y
2018-01-04 16:12:40.888353: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1237] 1:   Y Y
2018-01-04 16:12:40.888439: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1300] Adding visible gpu device 0
2018-01-04 16:12:40.888452: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1300] Adding visible gpu device 1
2018-01-04 16:12:41.384165: I tensorflow/core/common_runtime/gpu/gpu_device.cc:987] Creating TensorFlow device (/job:localhost/replica:0/task:0/device:GPU:0 with 10413 MB memory) -> physical GPU (device: 0, name: GeForce GTX 1080 Ti, pci bus id: 0000:02:00.0, compute capability: 6.1)
2018-01-04 16:12:41.487240: I tensorflow/core/common_runtime/gpu/gpu_device.cc:987] Creating TensorFlow device (/job:localhost/replica:0/task:0/device:GPU:1 with 10413 MB memory) -> physical GPU (device: 1, name: GeForce GTX 1080 Ti, pci bus id: 0000:03:00.0, compute capability: 6.1)

In [4]: sess.run(hello)
Out[4]: b'Hello, TensorFlow!'

In [5]: a = tf.constant(10)

In [6]: b = tf.constant(32)

In [7]: sess.run(a + b)
Out[7]: 42

In [8]: sess.close()

In [9]:
```

