FROM nathanesaunlsn/compile_docs:ubuntu2004_protobuf_c

# install ssl, etc.
RUN apt-get update
RUN apt-get -y install libssl-dev
RUN apt-get -y install cmake

# build nats.c
RUN git clone https://github.com/nats-io/nats.c
RUN cd nats.c && mkdir build
RUN cd nats.c && cd build && cmake ..
RUN cd nats.c && cd build && make
RUN cd nats.c && cd build && make install
