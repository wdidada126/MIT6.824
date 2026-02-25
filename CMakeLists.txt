cmake_minimum_required(VERSION 3.10)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(BusTub
        VERSION 2022.8
        DESCRIPTION "The BusTub Relational Database Management System (Educational) @ https://github.com/cmu-db/bustub"
        LANGUAGES C CXX
)

add_subdirectory(src/kvRaft)
#add_subdirectory(src/MapReduce)
#add_subdirectory(src/Raft)
#add_subdirectory(src/shardKv)