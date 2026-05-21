cmake_minimum_required(VERSION 3.10)

project(WebServer)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_CXX_FLAGS
        "${CMAKE_CXX_FLAGS} -g -Wall"
)

# 头文件目录
include_directories(
        ${PROJECT_SOURCE_DIR}/../src/base
        ${PROJECT_SOURCE_DIR}/../src/net
        ${PROJECT_SOURCE_DIR}/../src/net/poller
        ${PROJECT_SOURCE_DIR}/../src/http
        ${PROJECT_SOURCE_DIR}/../src/timer
        ${PROJECT_SOURCE_DIR}/../src/logger
        ${PROJECT_SOURCE_DIR}/../src/memory
        ${PROJECT_SOURCE_DIR}/../src/mysql
)

# 动态库目录
link_directories(
        ${PROJECT_SOURCE_DIR}/../lib
)

# 编译程序
add_executable(WebServer
        main.cc
)

# 链接 tiny_network
target_link_libraries(WebServer
        tiny_network
        pthread
        mysqlclient
)