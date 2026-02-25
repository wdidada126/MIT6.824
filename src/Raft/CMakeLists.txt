# 定义源文件
set(raft_SOURCES
        raft.cpp
)

# 创建可执行文件
add_executable(raft ${raft_SOURCES})
target_link_libraries(raft
        zmq
        pthread
        rt)