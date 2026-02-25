project(MapReduceFunc VERSION 1.0.0 LANGUAGES CXX)

# 设置 C++ 标准
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# 设置输出目录
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# 设置编译选项
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -O2")

# 添加共享库（对应你的 libmrFunc.so）
add_library(mrFunc SHARED
        map_reduceFun.cpp
)

# 设置库的属性
set_target_properties(mrFunc PROPERTIES
        OUTPUT_NAME "mrFunc"          # 库文件名为 libmrFunc.so
        VERSION ${PROJECT_VERSION}    # 版本号
        SOVERSION 1                   # API 版本
        POSITION_INDEPENDENT_CODE ON  # 相当于 -fpic
)

# 添加头文件搜索路径（如果有头文件）
target_include_directories(mrFunc PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}
        ${CMAKE_CURRENT_BINARY_DIR}
)

# 添加链接库（如果有依赖）
# target_link_libraries(mrFunc PRIVATE
#     some_library
# )

# 如果需要生成位置无关代码（PIC），默认 SHARED 库会自动添加 -fPIC
# 但也可以显式设置：
# set_property(TARGET mrFunc PROPERTY POSITION_INDEPENDENT_CODE ON)

# 可选：添加测试可执行文件
# add_executable(test_mrFunc test_mrFunc.cpp)
# target_link_libraries(test_mrFunc PRIVATE mrFunc)

# 安装规则（可选）
install(TARGETS mrFunc
        LIBRARY DESTINATION lib       # 安装到系统 lib 目录
        ARCHIVE DESTINATION lib       # 静态库
        RUNTIME DESTINATION bin       # Windows DLL
)

install(FILES map_reduceFun.h     # 如果有头文件
        DESTINATION include
)


set(master_SOURCES
        master.cpp
)
add_executable(master ${master_SOURCES})
target_link_libraries(master
        zmq
        pthread
        rt)