# Docker (CentOS 7.3)

Last updated: Feb 8, 2021.

## Compile Instructions

```bash
docker run -it --rm nathanesaunlsn/compile_docs:centos73_protobuf /bin/bash

# install cmake
yum -y install cmake

# output
mkdir /protobuf_c_install

# build protobuf-c
git clone https://github.com/protobuf-c/protobuf-c
cd protobuf-c
git submodule update --init --recursive
./autogen.sh
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
./configure
make
make install
```

## Create docker image

```bash
cd centos73

# takes about 2 minutes to build
docker build -t centos73_protobuf_c .

# upload image to dockerhub
# requires logging into dockerhub first
docker tag centos73_protobuf_c nathanesaunlsn/compile_docs:centos73_protobuf_c
docker push nathanesaunlsn/compile_docs:centos73_protobuf_c
```

## Using docker image

```bash
docker pull nathanesaunlsn/compile_docs:centos73_protobuf_c

# do what you want
# i.e. copy binaries
# i.e. build nats.c
# etc.
docker run -it --rm nathanesaunlsn/compile_docs:centos73_protobuf_c /bin/bash
```