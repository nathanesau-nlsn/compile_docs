## Docker (Ubuntu 20.04)

Last updated: Feb 8, 2021.

## Compile Instructions

```bash
docker run -it --rm nathanesaunlsn/compile_docs:ubuntu2004_protobuf /bin/bash

# update
apt-get update

# build protobuf-c
git clone https://github.com/protobuf-c/protobuf-c
cd protobuf-c
git submodule update --init --recursive
./autogen.sh
./configure
make
make install
```

## Creating docker image

```bash
cd ubuntu2004

# takes about 2 minutes to build
docker build -t ubuntu2004_protobuf_c .

# upload image to dockerhub
# requires logging into dockerhub first
docker tag ubuntu2004_protobuf_c nathanesaunlsn/compile_docs:ubuntu2004_protobuf_c
docker push nathanesaunlsn/compile_docs:ubuntu2004_protobuf_c
```

## Using docker image

```bash
docker pull nathanesaunlsn/compile_docs:ubuntu2004_protobuf_c

# do what you want
# i.e. copy binaries
# i.e. build nats.c
# etc.
docker run -it --rm nathanesaunlsn/compile_docs:ubuntu2004_protobuf_c /bin/bash
```