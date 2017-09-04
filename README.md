# install Tensorflow with GPU support on Centos 7

## system: fully installed Centos 7
* system update

```sh
$ sudo yum -y update
$ sudo yum -y install epel-release
$ sudo yum -y install gcc gcc-c++ python-pip python-devel atlas atlas-devel gcc-gfortran openssl-devel libffi-devel
```

## Install CUDA following the guide from http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#axzz4rhm3n5RO
* Install GPU driver
```sh
$ sudo rpm --install cuda-repo-<distro>-<version>.<architecture>.rpm
$ sudo yum clean expire-cache
$ sudo yum install cuda
```

* Install CUDA® Toolkit 8.0 
```sh
$ download from https://developer.nvidia.com/cuda-downloads
$ sudo sh cuda_8.0.61_375.26_linux.run
  Do you accept the previously read EULA?
  accept/decline/quit: accept
  Install NVIDIA Accelerated Graphics Driver for Linux-x86_64 375.26?
  (y)es/(n)o/(q)uit: n
  Install the CUDA 8.0 Toolkit?
  (y)es/(n)o/(q)uit: y
  Enter Toolkit Location
  [ default is /usr/local/cuda-8.0 ]: 
  Do you want to install a symbolic link at /usr/local/cuda?
  (y)es/(n)o/(q)uit: y
  Install the CUDA 8.0 Samples?
  (y)es/(n)o/(q)uit: y
  Enter CUDA Samples Location
  [ default is /home/XXXXX ]: 
```
## Install CUDNN 
* install CUDNN
```sh
$ download from https://developer.nvidia.com/rdp/cudnn-download
$ tar zxf cudnn-8.0-linux-x64-v6.0.solitairetheme8
$ sudo cp cuda/include/cudnn.h /usr/local/cuda-8.0/include/
$ sudo cp cuda/lib64/libcudnn* /usr/local/cuda-8.0/lib64/.
$ sudo chmod a+x /usr/local/cuda-8.0/include/cudnn.h /usr/local/cuda-8.0/lib64/libcudnn*
```
## edit .bashrc file
add the following lines into your .bashrc file
```sh
export PATH=/usr/local/cuda-8.0/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64\
                         ${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
export CUDA_HOME=/usr/local/cuda
```

## install Tensorflow with pip
```sh
$ sudo pip install --upgrade pip
$ sudo pip install tensorflow-gpu
$ sudo pip install ipython
```

## Check Tensorflow with ipython
```sh
$ ipython
Python 2.7.5 (default, Nov  6 2016, 00:28:07) 
Type "copyright", "credits" or "license" for more information.

IPython 5.4.1 -- An enhanced Interactive Python.
?         -> Introduction and overview of IPython's features.
%quickref -> Quick reference.
help      -> Python's own help system.
object?   -> Details about 'object', use 'object??' for extra details.

In [1]: import tensorflow as tf

In [2]: sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))
2017-09-04 19:01:54.085247: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.1 instructions, but these are available on your machine and could speed up CPU computations.
2017-09-04 19:01:54.085335: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.2 instructions, but these are available on your machine and could speed up CPU computations.
2017-09-04 19:01:54.085354: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX instructions, but these are available on your machine and could speed up CPU computations.
2017-09-04 19:01:54.085418: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX2 instructions, but these are available on your machine and could speed up CPU computations.
2017-09-04 19:01:54.085439: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use FMA instructions, but these are available on your machine and could speed up CPU computations.
2017-09-04 19:01:56.229195: I tensorflow/core/common_runtime/gpu/gpu_device.cc:955] Found device 0 with properties: 
name: GeForce GTX 1080 Ti
major: 6 minor: 1 memoryClockRate (GHz) 1.62
pciBusID 0000:04:00.0
Total memory: 10.91GiB
Free memory: 10.75GiB
2017-09-04 19:01:56.546687: W tensorflow/stream_executor/cuda/cuda_driver.cc:523] A non-primary context 0x5e8c1d0 exists before initializing the StreamExecutor. We haven't verified StreamExecutor works with that.
2017-09-04 19:01:56.547740: I tensorflow/core/common_runtime/gpu/gpu_device.cc:955] Found device 1 with properties: 
name: GeForce GTX 1080 Ti
major: 6 minor: 1 memoryClockRate (GHz) 1.62
pciBusID 0000:81:00.0
Total memory: 10.91GiB
Free memory: 10.75GiB
2017-09-04 19:01:56.547901: I tensorflow/core/common_runtime/gpu/gpu_device.cc:847] Peer access not supported between device ordinals 0 and 1
2017-09-04 19:01:56.547928: I tensorflow/core/common_runtime/gpu/gpu_device.cc:847] Peer access not supported between device ordinals 1 and 0
2017-09-04 19:01:56.547961: I tensorflow/core/common_runtime/gpu/gpu_device.cc:976] DMA: 0 1 
2017-09-04 19:01:56.547978: I tensorflow/core/common_runtime/gpu/gpu_device.cc:986] 0:   Y N 
2017-09-04 19:01:56.547999: I tensorflow/core/common_runtime/gpu/gpu_device.cc:986] 1:   N Y 
2017-09-04 19:01:56.548040: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1045] Creating TensorFlow device (/gpu:0) -> (device: 0, name: GeForce GTX 1080 Ti, pci bus id: 0000:04:00.0)
2017-09-04 19:01:56.548059: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1045] Creating TensorFlow device (/gpu:1) -> (device: 1, name: GeForce GTX 1080 Ti, pci bus id: 0000:81:00.0)
Device mapping:
/job:localhost/replica:0/task:0/gpu:0 -> device: 0, name: GeForce GTX 1080 Ti, pci bus id: 0000:04:00.0
/job:localhost/replica:0/task:0/gpu:1 -> device: 1, name: GeForce GTX 1080 Ti, pci bus id: 0000:81:00.0
2017-09-04 19:01:56.795901: I tensorflow/core/common_runtime/direct_session.cc:300] Device mapping:
/job:localhost/replica:0/task:0/gpu:0 -> device: 0, name: GeForce GTX 1080 Ti, pci bus id: 0000:04:00.0
/job:localhost/replica:0/task:0/gpu:1 -> device: 1, name: GeForce GTX 1080 Ti, pci bus id: 0000:81:00.0

```

##Now everything is done!

##Appendix
If you meet the following bug report
```sh 
$ nvidia-smi
  Unable to determine the device handle for GPU 0000:81:00.0: Unable to communicate with GPU because it is insufficiently powered.
This may be because not all required external power cables are
attached, or the attached cables are not seated properly.
```
then you should check your power supply of the GPU. 
This is not a software problem.

Please do not intsll the GPU driver from CUDA® Toolkit 8.0.

