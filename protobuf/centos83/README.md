# Docker (CentOS 8.3)

Last updated: Feb 9, 2021.

## Compile Instructions

```bash
docker run -it --rm centos:centos8.3.2011 /bin/bash

# install git, etc.
yum -y install git
yum -y install autoconf
yum -y install automake
yum -y install pkgconfig
yum -y install libtool
yum -y install gcc-c++
yum -y install make

# output
mkdir /protobuf_install

# build protobuf
git clone https://github.com/google/protobuf.git
cd protobuf
git submodule update --init --recursive
./autogen.sh
./configure
make
make check
make install
ldconfig
```

## Creating Docker Image

```bash
cd centos83

# takes about 20 minutes to build
docker build -t centos83_protobuf .

# upload image to dockerhub
# requires logging into dockerhub first
docker tag centos83_protobuf nathanesaunlsn/compile_docs:centos83_protobuf
docker push nathanesaunlsn/compile_docs:centos83_protobuf
```

## Using Docker Image

```bash
docker pull nathanesaunlsn/compile_docs:centos83_protobuf

# do what you want
# i.e. copy binaries
# i.e. build protobuf-c
# etc.
docker run -it --rm nathanesaunlsn/compile_docs:centos83_protobuf /bin/bash
```