FROM nathanesaunlsn/compile_docs:centos73_protobuf

# output
RUN mkdir /protobuf_c_install

# build protobuf-c
RUN git clone https://github.com/protobuf-c/protobuf-c
RUN cd protobuf-c && git submodule update --init --recursive
RUN cd protobuf-c && ./autogen.sh
RUN export PKG_CONFIG_PATH=/protobuf_install/lib/pkgconfig && cd protobuf-c && ./configure --prefix=/protobuf_c_install --disable-shared
RUN export PKG_CONFIG_PATH=/protobuf_install/lib/pkgconfig && cd protobuf-c && make
RUN export PKG_CONFIG_PATH=/protobuf_install/lib/pkgconfig && cd protobuf-c && make install
