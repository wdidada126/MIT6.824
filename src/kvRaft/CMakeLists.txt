# 定义源文件
set(cli_SOURCES
        client.cpp
)

# 创建可执行文件
add_executable(cli ${cli_SOURCES})
target_link_libraries(cli
        zmq
        pthread
        rt)
set(server_SOURCES
        server.cpp
)

add_executable(ser ${server_SOURCES})
target_link_libraries(ser
        zmq
        pthread
        rt)
