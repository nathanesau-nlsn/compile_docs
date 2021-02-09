FROM centos:centos8.3.2011

# install git, etc.
RUN yum -y install git
RUN yum -y install autoconf
RUN yum -y install automake
RUN yum -y install pkgconfig
RUN yum -y install libtool
RUN yum -y install gcc-c++
RUN yum -y install make

# build protobuf
RUN git clone https://github.com/google/protobuf.git
RUN cd protobuf && git submodule update --init --recursive
RUN cd protobuf && ./autogen.sh
RUN cd protobuf && ./configure
RUN cd protobuf && make
RUN cd protobuf && make check
RUN cd protobuf && make install
RUN cd protobuf && ldconfig