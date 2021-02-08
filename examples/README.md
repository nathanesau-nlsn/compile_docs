# Instructions

## protobuf-examples

### Docker (Ubuntu 20.04)

```bash
# see https://github.com/protobuf-c/protobuf-c/wiki/Examples
docker run -it --rm -v "D:/compile_docs/examples/protobuf-examples":/protobuf-examples nathanesaunlsn/compile_docs:ubuntu2004_protobuf_c /bin/bash

# install cmake
apt-get -y install cmake
apt-get -y install protobuf-compiler

# build
cd protobuf-examples
mkdir build
cd build
cmake ..
make

# run the programs
./add_person_cpp
./list_people_cpp
```

### Docker (CentOS 7.3)

TO FIX!!! 
NOT WORKING

```bash
# see https://github.com/protobuf-c/protobuf-c/wiki/Examples
docker run -it --rm -v "D:/compile_docs/examples/protobuf-examples":/protobuf-examples nathanesaunlsn/compile_docs:centos73_protobuf_c /bin/bash

# install cmake
yum -y install cmake
yum -y install protobuf-compiler

# build
cd protobuf-examples
```

## natsc-examples

### Docker (Ubuntu 20.04)

```bash
# see https://github.com/nats-io/nats.c/tree/master/examples/getstarted
docker run -it --rm -v "D:/compile_docs/examples/natsc-examples":/natsc-examples nathanesaunlsn/compile_docs:ubuntu2004_natsc /bin/bash

# install cmake
apt-get -y install cmake
apt-get -y install protobuf-compiler

# TODO add examples

# currently no examples in this repo, so use nats examples instead
cd nats.c
cd examples
cmake ..
make

# run the programs
cd examples
./nats-connect
./nats-replier
```

### Docker (CentOS 7.3)

TO FIX!!! 
NOT WORKING

```bash
# see https://github.com/nats-io/nats.c/tree/master/examples/getstarted

# install cmake
yum -y install cmake
yum -y install protobuf-compiler

# TODO add examples

# currently no examples in this repo, so use nats examples instead
cd nats.c
cd examples
cmake ..
make

# run the programs
cd examples
./nats-connect
./nats-replier
```
