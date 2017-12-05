# install Pytorch on Centos 7

## system: fully installed Centos 7
* system update
* CUDA® Toolkit 8.0 and cuDNN v6.0 are installed 

## Install Pytorch for python 2 with pip
* run the following commands
```sh
$ pip install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp27-cp27mu-manylinux1_x86_64.whl 
$ pip install torchvision 

# # if the above command does not work, then you have python 2.7 UCS2, use this command 
# $ pip install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp27-cp27m-manylinux1_x86_64.whl
```

* Install log
```sh
$ sudo pip install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp27-cp27mu-manylinux1_x86_64.whl 
Collecting torch==0.2.0.post3 from http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp27-cp27mu-manylinux1_x86_64.whl
  Downloading http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp27-cp27mu-manylinux1_x86_64.whl (487.1MB)
    100% |████████████████████████████████| 487.1MB 1.8MB/s 
Requirement already satisfied: pyyaml in /usr/lib64/python2.7/site-packages (from torch==0.2.0.post3)
Requirement already satisfied: numpy in /usr/lib64/python2.7/site-packages (from torch==0.2.0.post3)
Installing collected packages: torch
Successfully installed torch-0.2.0.post3
$ sudo pip install torchvision 
Collecting torchvision
  Downloading http://mirrors.aliyun.com/pypi/packages/e2/56/34a58783d2fefe2da5c4558c213386c810e7b2ab04dd8d6fe474a91b695a/torchvision-0.1.9-py2.py3-none-any.whl (43kB)
    100% |████████████████████████████████| 51kB 470kB/s 
Collecting pillow (from torchvision)
  Downloading http://mirrors.aliyun.com/pypi/packages/43/5a/904f2cc20ef9f9ba05f9ff1fb3dfadb1e6923e3bf6f8c8363d5dc3a179ab/Pillow-4.2.1-cp27-cp27mu-manylinux1_x86_64.whl (5.8MB)
    100% |████████████████████████████████| 5.8MB 473kB/s 
Requirement already satisfied: torch in /usr/lib64/python2.7/site-packages (from torchvision)
Requirement already satisfied: six in /usr/lib/python2.7/site-packages (from torchvision)
Requirement already satisfied: numpy in /usr/lib64/python2.7/site-packages (from torchvision)
Collecting olefile (from pillow->torchvision)
  Downloading http://mirrors.aliyun.com/pypi/packages/35/17/c15d41d5a8f8b98cc3df25eb00c5cee76193114c78e5674df6ef4ac92647/olefile-0.44.zip (74kB)
    100% |████████████████████████████████| 81kB 491kB/s 
Requirement already satisfied: pyyaml in /usr/lib64/python2.7/site-packages (from torch->torchvision)
Building wheels for collected packages: olefile
  Running setup.py bdist_wheel for olefile ... done
  Stored in directory: /root/.cache/pip/wheels/08/c9/45/7f7ae2cf8e7f278be9f6d3af7fe35b3c03505ece05453db9e1
Successfully built olefile
Installing collected packages: olefile, pillow, torchvision
Successfully installed olefile-0.44 pillow-4.2.1 torchvision-0.1.9
```

## Install Pytorch for python 3 with conda 

```sh
[liangyu@localhost ~]$ conda list
# packages in environment at /miniconda3:
#
asn1crypto                0.22.0                   py36_0  
bleach                    1.5.0                     <pip>
cffi                      1.10.0                   py36_0  
conda                     4.3.25                   py36_0  
conda-env                 2.6.0                         0  
cryptography              1.8.1                    py36_0  
cycler                    0.10.0                    <pip>
decorator                 4.1.2                     <pip>
html5lib                  0.9999999                 <pip>
idna                      2.5                      py36_0  
ipython                   6.1.0                     <pip>
ipython-genutils          0.2.0                     <pip>
jedi                      0.10.2                    <pip>
Keras                     2.0.8                     <pip>
libffi                    3.2.1                         1  
Markdown                  2.6.9                     <pip>
matplotlib                2.0.2                     <pip>
mkl                       2017.0.3                      0  
numpy                     1.13.1                    <pip>
openssl                   1.0.2l                        0  
packaging                 16.8                     py36_0  
pandas                    0.20.3                    <pip>
pexpect                   4.2.1                     <pip>
pickleshare               0.7.4                     <pip>
pip                       9.0.1                    py36_1  
prompt-toolkit            1.0.15                    <pip>
protobuf                  3.4.0                     <pip>
ptyprocess                0.5.2                     <pip>
pycosat                   0.6.2                    py36_0  
pycparser                 2.17                     py36_0  
Pygments                  2.2.0                     <pip>
pyopenssl                 17.0.0                   py36_0  
pyparsing                 2.1.4                    py36_0  
python                    3.6.1                         2  
python-dateutil           2.6.1                     <pip>
pytz                      2017.2                    <pip>
PyYAML                    3.12                      <pip>
readline                  6.2                           2  
requests                  2.14.2                   py36_0  
ruamel_yaml               0.11.14                  py36_1  
scikit-learn              0.19.0                    <pip>
scipy                     0.19.1                    <pip>
setuptools                27.2.0                   py36_0  
simplegeneric             0.8.1                     <pip>
six                       1.10.0                   py36_0  
sqlite                    3.13.0                        0  
tensorflow                1.3.0                     <pip>
tensorflow-tensorboard    0.1.5                     <pip>
tk                        8.5.18                        0  
traitlets                 4.3.2                     <pip>
wcwidth                   0.1.7                     <pip>
Werkzeug                  0.12.2                    <pip>
wheel                     0.29.0                   py36_0  
xz                        5.2.2                         1  
yaml                      0.1.6                         0  
zlib                      1.2.8                         3  
$ pip list --format=columns        
Package                Version  
---------------------- ---------
asn1crypto             0.22.0   
bleach                 1.5.0    
cffi                   1.10.0   
conda                  4.3.25   
cryptography           1.8.1    
cycler                 0.10.0   
decorator              4.1.2    
html5lib               0.9999999
idna                   2.5      
ipython                6.1.0    
ipython-genutils       0.2.0    
jedi                   0.10.2   
Keras                  2.0.8    
Markdown               2.6.9    
matplotlib             2.0.2    
numpy                  1.13.1   
packaging              16.8     
pandas                 0.20.3   
pexpect                4.2.1    
pickleshare            0.7.4    
pip                    9.0.1    
prompt-toolkit         1.0.15   
protobuf               3.4.0    
ptyprocess             0.5.2    
pycosat                0.6.2    
pycparser              2.17     
Pygments               2.2.0    
pyOpenSSL              17.0.0   
pyparsing              2.1.4    
python-dateutil        2.6.1    
pytz                   2017.2   
PyYAML                 3.12     
requests               2.14.2   
scikit-learn           0.19.0   
scipy                  0.19.1   
setuptools             27.2.0   
simplegeneric          0.8.1    
six                    1.10.0   
tensorflow             1.3.0    
tensorflow-tensorboard 0.1.5    
traitlets              4.3.2    
wcwidth                0.1.7    
Werkzeug               0.12.2   
wheel                  0.29.0  
```
* run the following commands
```sh
$ sudo /miniconda3/bin/pip install cffi numpy pyyam
$ sudo /miniconda3/bin/conda install mkl
$ sudo /miniconda3/bin/conda install -c soumith magma-cuda80
$ sudo /miniconda3/bin/conda install -c soumith cuda80


 sudo /miniconda3/bin/conda install pytorch torchvision cuda80 -c soumith
[sudo] password for liangyu:
Fetching package metadata ...........
Solving package specifications: .

Package plan for installation in environment /miniconda3:

The following NEW packages will be INSTALLED:

    freetype:    2.5.5-2
    jbig:        2.1-0
    jpeg:        9b-0
    libgcc:      5.2.0-0
    libpng:      1.6.30-1
    libtiff:     4.0.6-3
    numpy:       1.13.1-py36_0
    olefile:     0.44-py36_0
    pillow:      4.2.1-py36_0
    pytorch:     0.2.0-py36h53baedd_4cu80 soumith [cuda80]
    torchvision: 0.1.9-py36h7584368_1     soumith

Proceed ([y]/n)? y

$ sudo /miniconda3/bin/conda install freetype jbig jpeg libgcc libpng libtiff numpy olefile pillow
$ sudo /miniconda3/bin/conda install pytorch torchvision cuda80 -c soumith