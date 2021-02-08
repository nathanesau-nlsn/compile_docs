FROM centos:centos7.3.1611

# install git, etc.
RUN yum -y install git
RUN yum -y install autoconf
RUN yum -y install automake
RUN yum -y install pkgconfig
RUN yum -y install libtool
RUN yum -y install gcc-c++
RUN yum -y install make

# output
RUN mkdir /protobuf_install

# build protobuf
RUN git clone https://github.com/google/protobuf.git
RUN cd protobuf && git submodule update --init --recursive
RUN cd protobuf && ./autogen.sh
RUN cd protobuf && ./configure --prefix=/protobuf_install --disable-shared
RUN cd protobuf && make
RUN cd protobuf && make check
RUN cd protobuf && make install
RUN cd protobuf && ldconfig