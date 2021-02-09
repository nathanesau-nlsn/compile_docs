#-- Install configuration: "Release"
#-- Up-to-date: /usr/local/lib64/pkgconfig/libnats.pc
#-- Installing: /usr/local/lib64/libnats.so.2.3.0
#-- Up-to-date: /usr/local/lib64/libnats.so.2.3
#-- Up-to-date: /usr/local/lib64/libnats.so
#-- Removed runtime path from "/usr/local/lib64/libnats.so.2.3.0"
#-- Up-to-date: /usr/local/lib/cmake/cnats/cnats-config.cmake
#-- Installing: /usr/local/lib/cmake/cnats/cnats-config-release.cmake
#-- Installing: /usr/local/lib64/libnats_static.a
#-- Up-to-date: /usr/local/lib/cmake/cnats/cnats-config.cmake
#-- Up-to-date: /usr/local/lib/cmake/cnats/cnats-config-release.cmake
#-- Up-to-date: /usr/local/include/nats.h
#-- Up-to-date: /usr/local/include/nats/nats.h
#-- Up-to-date: /usr/local/include/nats/status.h
#-- Up-to-date: /usr/local/include/nats/version.h
#-- Up-to-date: /usr/local/include/nats/adapters/libevent.h
#-- Up-to-date: /usr/local/include/nats/adapters/libuv.h
cmake_minimum_required(VERSION 2.8.12)

project(main)

find_package(cnats REQUIRED)
include_directories(${cnats_INCLUDE_DIR})

add_executable(main
    main.cpp
)

target_link_libraries(main LINK_PUBLIC cnats::nats)
