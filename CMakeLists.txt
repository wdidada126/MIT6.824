cmake_minimum_required(VERSION 3.10)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(MIT6.824_cpp
        VERSION 2022.8
        DESCRIPTION "MIT6.824_cpp"
        LANGUAGES C CXX
)

# 检测操作系统
if(CMAKE_SYSTEM_NAME STREQUAL "Linux")
    add_subdirectory(src/kvRaft)
    add_subdirectory(src/MapReduce)
    add_subdirectory(src/Raft)
    add_subdirectory(src/shardKv)
else()
    message(STATUS "${CMAKE_SYSTEM_NAME} 系统，跳过 Linux 专用模块")
endif()