cmake_minimum_required(VERSION 3.10)

project(QHttp)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(THREADS_PREFER_PTHREAD_FLAG ON)
set(CMAKE_DISABLE_SOURCE_CHANGES ON)
set(CMAKE_AUTOMOC ON)

find_package(Qt5 COMPONENTS Core Network REQUIRED)

add_library(qhttp
    3rdparty/http-parser/http_parser.c
    3rdparty/http-parser/http_parser.h
    src/qhttpabstracts.cpp
    src/qhttpserverconnection.cpp
    src/qhttpserverrequest.cpp
    src/qhttpserverresponse.cpp
    src/qhttpserver.cpp
    src/qhttpfwd.hpp
    src/qhttpabstracts.hpp
    src/qhttpserverconnection.hpp
    src/qhttpserverrequest.hpp
    src/qhttpserverresponse.hpp
    src/qhttpserver.hpp
    src/qhttpclientrequest.cpp
    src/qhttpclientresponse.cpp
    src/qhttpclient.cpp
    src/qhttpclient.hpp
    src/qhttpclientresponse.hpp
    src/qhttpclientrequest.hpp
)
target_compile_definitions(qhttp PRIVATE QHTTP_EXPORT)
target_compile_definitions(qhttp PRIVATE QHTTP_HAS_CLIENT)
target_link_libraries(qhttp PUBLIC Qt5::Core Qt5::Network)
target_include_directories(qhttp PRIVATE 3rdparty src/private)
target_include_directories(qhttp PUBLIC src)
