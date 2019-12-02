set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)

# 配置引用的头文件
# INCLUDE_DIRECTORIES([AFTER|BEFORE] [SYSTEM] dir1 dir2 ...)
include_directories(${PROJECT_SOURCE_DIR}/lib)

# 链接动态库
# LINK_DIRECTORIES 和 TARGET_LINK_LIBRARIES

# LINK_DIRECTORIES(directory1 directory2 ...)
# 配置查找链接库的路径
link_directories(${PROJECT_BINARY_DIR}/lib)

add_executable(example1 main.cpp)
target_link_libraries(example1 hellolib)

add_executable(example2 main2.cpp)
target_link_libraries(example2 libhellolib.a)

install(TARGETS example1 example2 DESTINATION bin)