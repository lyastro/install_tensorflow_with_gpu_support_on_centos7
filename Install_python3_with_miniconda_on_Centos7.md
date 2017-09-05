# install python3 with miniconda on Centos 7

## system: fully installed Centos 7
* system update

## Install miniconda
* Download miniconda from https://conda.io/miniconda.html
```sh
$ wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

* Install miniconda as root
```sh
$ sudo sh Miniconda3-latest-Linux-x86_64.sh

Welcome to Miniconda3 4.3.21 (by Continuum Analytics, Inc.)

In order to continue the installation process, please review the license
agreement.
Please, press ENTER to continue
>>> 
===================================
Anaconda End User License Agreement
===================================

Copyright 2017, Continuum Analytics, Inc.

All rights reserved under the 3-clause BSD License:

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

* Redistributions of source code must retain the above copyright notice,
this list of conditions and the following disclaimer.
* Redistributions in binary form must reproduce the above copyright notice,
this list of conditions and the following disclaimer in the documentation
and/or other materials provided with the distribution.
* Neither the name of Continuum Analytics, Inc. ("Continuum") nor the names
of its contributors may be used to endorse or promote products derived from
this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
ARE DISCLAIMED. IN NO EVENT SHALL CONTINUUM ANALYTICS, INC. BE LIABLE FOR
ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY
OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH
DAMAGE.


Notice of Third Party Software Licenses
=======================================

Anaconda contains open source software packages from third parties. These
are available on an "as is" basis and subject to their individual license
agreements. These licenses are available in Anaconda or at
http://docs.continuum.io/anaconda/pkg-docs . Any binary packages of these
third party tools you obtain via Anaconda are subject to their individual
licenses as well as the Anaconda license. Continuum Analytics ("Continuum")
reserves the right to change which third party tools are provided in
Anaconda.

In particular, Anaconda contains re-distributable, run-time, shared-library
files from the Intel(TM) Math Kernel Library ("MKL binaries"). You are
specifically authorized to use the MKL binaries with your installation of
Anaconda. You are also authorized to redistribute the MKL binaries with
Anaconda or in the conda package that contains them. Use and redistribution
of the MKL binaries are subject to the licensing terms located at
https://software.intel.com/en-us/license/intel-simplified-software-license.
If needed, instructions for removing the MKL binaries after installation of
Anaconda are available at http://www.continuum.io.

Anaconda also contains cuDNN software binaries from NVIDIA Corporation
("cuDNN binaries"). You are specifically authorized to use the cuDNN
binaries with your installation of Anaconda. You are also authorized to

Do you approve the license terms? [yes|no]
>>> yes

Miniconda3 will now be installed into this location:
/root/miniconda3

  - Press ENTER to confirm the location
  - Press CTRL-C to abort the installation
  - Or specify a different location below

[/root/miniconda3] >>> /miniconda3
PREFIX=/miniconda3
installing: python-3.6.1-2 ...
installing: asn1crypto-0.22.0-py36_0 ...
installing: cffi-1.10.0-py36_0 ...
installing: conda-env-2.6.0-0 ...
installing: cryptography-1.8.1-py36_0 ...
installing: idna-2.5-py36_0 ...
installing: libffi-3.2.1-1 ...
installing: openssl-1.0.2l-0 ...
installing: packaging-16.8-py36_0 ...
installing: pycosat-0.6.2-py36_0 ...
installing: pycparser-2.17-py36_0 ...
installing: pyopenssl-17.0.0-py36_0 ...
installing: pyparsing-2.1.4-py36_0 ...
installing: readline-6.2-2 ...
installing: requests-2.14.2-py36_0 ...
installing: ruamel_yaml-0.11.14-py36_1 ...
installing: setuptools-27.2.0-py36_0 ...
installing: six-1.10.0-py36_0 ...
installing: sqlite-3.13.0-0 ...
installing: tk-8.5.18-0 ...
installing: xz-5.2.2-1 ...
installing: yaml-0.1.6-0 ...
installing: zlib-1.2.8-3 ...
installing: conda-4.3.21-py36_0 ...
installing: pip-9.0.1-py36_1 ...
installing: wheel-0.29.0-py36_0 ...
Python 3.6.1 :: Continuum Analytics, Inc.
creating default environment...
installation finished.
Do you wish the installer to prepend the Miniconda3 install location
to PATH in your /root/.bashrc ? [yes|no]
[no] >>> yes

Prepending PATH=/miniconda3/bin to PATH in /root/.bashrc
A backup will be made to: /root/.bashrc-miniconda3.bak


For this change to become active, you have to open a new terminal.

Thank you for installing Miniconda3!

Share your notebooks and packages on Anaconda Cloud!
Sign up for free: https://anaconda.org


```

## Now the default pip is for python3!
* the default pip for sudo is still python2
* use the full path /miniconda/bin/pip when sudo
