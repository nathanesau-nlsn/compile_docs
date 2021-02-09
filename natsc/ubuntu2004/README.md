# Docker (Ubuntu 20.04)

Last updated: Feb 8, 2021.

## Compile Instructions

```bash
docker run -it --rm nathanesaunlsn/compile_docs:ubuntu2004_protobuf_c /bin/bash

# install ssl, etc.
apt-get update
apt-get -y install libssl-dev
apt-get -y install cmake

# for debugging
# docker cp F:/compile_docs/natsc/centos73/CMakeLists.txt pedantic_diffie:/nats.c/CMakeLists.txt

# build nats.c
git clone https://github.com/nats-io/nats.c
cd nats.c
mkdir build
cd build
cmake ..
make
make install
```

## Creating docker image

```bash
cd ubuntu2004

# takes about 2 minutes to build
docker build -t ubuntu2004_natsc .

# upload image to dockerhub
# requires logging into dockerhub first
docker tag ubuntu2004_natsc nathanesaunlsn/compile_docs:ubuntu2004_natsc
docker push nathanesaunlsn/compile_docs:ubuntu2004_natsc
```

## Using docker image

```bash
docker pull nathanesaunlsn/compile_docs:ubuntu2004_natsc

# do what you want
docker run -it --rm nathanesaunlsn/compile_docs:ubuntu2004_natsc /bin/bash
```

## Debugging

Following information will be removed later.

-- NATS_PROTOBUF_INCLUDE_DIR=/usr/local/include
    - contains google/protobuf, google/protobuf-c.h, protobuf-c/protobuf-c.h

-- NATS_PROTOBUF_LIBRARY=/usr/local/lib/libprotobuf-c.so

-- NATS_PROTOBUF_LIBRARY=/usr/local/lib/libprotobuf-c.so
-- NATS_PROTOBUF_INCLUDE_DIR=/usr/local/include
-- NATS_PROTOBUF_DIR=

For centos they should be:

set(NATS_PROTOBUF_LIBRARY, "/protobuf_c_install/lib/libprotobuf-c.so")

set(NATS_PROTOBUF_INCLUDE_DIR, "/protobuf_c_install/include")
