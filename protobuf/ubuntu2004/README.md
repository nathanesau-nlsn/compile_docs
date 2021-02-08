# Docker (Ubuntu 20.04)

Last updated: Feb 8, 2021.

## Compile instructions

```bash
docker run -it --rm ubuntu:20.04 /bin/bash

# install git, etc.
apt-get update
apt-get -y install git
apt-get -y install autoconf
apt-get -y install automake
apt-get -y install pkg-config
apt-get -y install libtool
apt-get -y install g++
apt-get -y install clang
apt-get -y install make

# build protobuf
git clone https://github.com/google/protobuf.git
cd protobuf
git submodule update --init --recursive
./autogen.sh
./configure --disable-dependency-tracking
make
make check
make install
ldconfig
```

## Creating docker image

```bash
cd ubuntu2004

# takes about 20 minutes to build
docker build -t ubuntu2004_protobuf .

# upload image to dockerhub
# requires logging into dockerhub first
docker tag ubuntu2004_protobuf nathanesaunlsn/compile_docs:ubuntu2004_protobuf
docker push nathanesaunlsn/compile_docs:ubuntu2004_protobuf
```

## Using docker image

```bash
docker pull nathanesaunlsn/compile_docs:ubuntu2004_protobuf

# do what you want
# i.e. copy binaries
# i.e. build protobuf-c
# etc.
docker run -it --rm nathanesaunlsn/compile_docs:ubuntu2004_protobuf /bin/bash
```
