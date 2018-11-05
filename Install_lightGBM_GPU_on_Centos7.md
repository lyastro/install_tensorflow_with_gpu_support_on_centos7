#install lightGBM from source with GPU support

CUDA is well installed.

## install boost

```sh
$ wget https://dl.bintray.com/boostorg/release/1.66.0/source/boost_1_66_0.tar.gz
$ tar zxf boost_1_66_0.tar.gz
$ cd boost_1_66_0
$ ./bootstrap.sh
$ sudo ./b2 install
```


## insatll cmake

```sh
sudo yum install cmake3 -y
$ sudo ln -s /usr/bin/cmake3 /usr/bin/cmake
```

## install lightGBM

```sh
$ git clone --recursive https://github.com/Microsoft/LightGBM ; cd LightGBM
$ mkdir build ; cd python-package
$ sudo /opt/anaconda/3/bin/python setup.py install --gpu  --opencl-include-dir=/usr/local/cuda/include/
```

# install xgboost

* build
```sh
$ git clone --recursive https://github.com/dmlc/xgboost
$ cd xgboost
$ mkdir build
$ cd build
$ cmake3 .. -DUSE_CUDA=ON
$ make -j
```

* install python package

```sh
cd ../python-package
sudo /opt/anaconda/3/bin/python setup.py install
```

* test

```sh
$ cd ../demo/gpu_acceleration/
$ python cover_type.py
```