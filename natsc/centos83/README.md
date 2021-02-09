# Docker (CentOS 7.3)

Last updated: Feb 9, 2021.

## Compile Instructions

```bash
docker run -it --rm nathanesaunlsn/compile_docs:centos83_protobuf_c /bin/bash

# install ssl, etc.
yum -y install openssl-devel
yum -y install cmake
yum -y install vim
yum -y install tree

# build nats.c
git clone https://github.com/nats-io/nats.c

# copy CMakeLists.txt to container
# see https://github.com/nats-io/nats.c/issues/297

cd nats.c
mkdir build
cd build
cmake ..
make
make install
```

## Creating docker image

```bash
cd centos83

# takes about 2 minutes to build
docker build -t centos83_natsc .

# upload image to dockerhub
# requires logging into dockerhub first
docker tag centos83_natsc nathanesaunlsn/compile_docs:centos83_natsc
docker push nathanesaunlsn/compile_docs:centos83_natsc
```

## Using docker image

```bash
docker pull nathanesaunlsn/compile_docs:centos83_natsc

# do what you want
docker run -it --rm nathanesaunlsn/compile_docs:centos83_natsc /bin/bash
```
