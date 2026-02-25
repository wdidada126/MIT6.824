# 定义源文件
set(cli_SOURCES
        client.cpp
)

# 创建可执行文件
add_executable(shardKv_cli ${cli_SOURCES})
target_link_libraries(shardKv_cli
        zmq
        pthread
        rt)
set(server_SOURCES
        server.cpp
)

add_executable(shardKv_ser ${server_SOURCES})
target_link_libraries(shardKv_ser
        zmq
        pthread
        rt)

set(test_SOURCES
        test.cpp
)

add_executable(test ${test_SOURCES})
target_link_libraries(test
        zmq
        pthread
        rt)
