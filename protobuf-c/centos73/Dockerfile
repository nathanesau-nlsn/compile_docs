FROM nathanesaunlsn/compile_docs:centos73_protobuf

# build protobuf-c
RUN git clone https://github.com/protobuf-c/protobuf-c
RUN cd protobuf-c && git submodule update --init --recursive
RUN cd protobuf-c && ./autogen.sh
RUN export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig && cd protobuf-c && ./configure
RUN export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig && cd protobuf-c && make
RUN export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig && cd protobuf-c && make install
