FROM nathanesaunlsn/compile_docs:ubuntu2004_protobuf

# update
RUN apt-get update

# build protobuf-c
RUN git clone https://github.com/protobuf-c/protobuf-c
RUN cd protobuf-c && git submodule update --init --recursive
RUN cd protobuf-c && ./autogen.sh
RUN cd protobuf-c && ./configure
RUN cd protobuf-c && make
RUN cd protobuf-c && make install
