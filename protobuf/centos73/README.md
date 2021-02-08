# Docker (CentOS 7.3)

Last updated: Feb 8, 2021.

## Compile Instructions

```bash
docker run -it --rm centos:centos7.3.1611 /bin/bash

# install git, etc.
yum -y install git
yum -y install autoconf
yum -y install automake
yum -y install pkgconfig
yum -y install libtool
yum -y install gcc-c++
yum -y install make

# build protobuf
git clone https://github.com/google/protobuf.git
cd protobuf
git submodule update --init --recursive
./autogen.sh

# SHOULD BE ./configure --disable-shared
# WITH GCC9???
./configure
make
make check
make install
ldconfig
```

## Creating Docker Image

```bash
cd centos73

# takes about 20 minutes to build
docker build -t centos73_protobuf .

# upload image to dockerhub
# requires logging into dockerhub first
docker tag centos73_protobuf nathanesaunlsn/compile_docs:centos73_protobuf
docker push nathanesaunlsn/compile_docs:centos73_protobuf
```
