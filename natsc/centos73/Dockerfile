FROM nathanesaunlsn/compile_docs:centos73_protobuf_c

# install ssl, etc.
RUN yum -y install openssl-devel
RUN yum -y install cmake
RUN yum -y install protobuf

# build nats.c
RUN git clone https://github.com/nats-io/nats.c
RUN cd nats.c && mkdir build

# TO FIX!!!
# NOT WORKING
RUN cd nats.c && cd build && cmake ..
RUN cd nats.c && cd build && make
RUN cd nats.c && cd build && make install