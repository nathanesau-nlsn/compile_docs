FROM ubuntu:20.04

# install git, etc.
RUN apt-get update
RUN apt-get -y install git
RUN apt-get -y install autoconf
RUN apt-get -y install automake
# see https://serverfault.com/questions/949991/how-to-install-tzdata-on-a-ubuntu-docker-image
RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install pkg-config
RUN apt-get -y install libtool
RUN apt-get -y install g++
RUN apt-get -y install clang
RUN apt-get -y install make

# build protobuf
RUN git clone https://github.com/google/protobuf.git
RUN cd protobuf && git submodule update --init --recursive
RUN cd protobuf && ./autogen.sh
RUN cd protobuf && ./configure --disable-dependency-tracking
RUN cd protobuf && make
RUN cd protobuf && make check
RUN cd protobuf && make install

# run ldconfig
RUN cd protobuf && ldconfig
