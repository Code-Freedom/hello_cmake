# PROJECT(projectname, [CXX] [C] [Java])
# 隐含定义了两个变量 <projectname>_SOURCE_DIR 和 <projectname>_BINARY_DIR
# 通常情况下，值与 PROJECT_SOURCE_DIR 和 PROJECT_BINARY_DIR 相同
PROJECT(HELLO)

# SET(VAR [VALUE] [CACHE TYPE DOCSTRING [FORCE]]) 
# 用来显式的定义变量
# 定义多个文件 SET(SRC_LIST main.cpp t1.cpp t2.cpp)
SET(SRC_LIST main.cpp)

# MESSAGE([SEND_ERROR | STATUS | FATAL_ERROR] "xxx" ...)
MESSAGE(STATUS "This is BINARY dir" ${HELLO_BINARY_DIR})
MESSAGE(STATUS "THIS is SOURCE dir" ${HELLO_SOURCE_DIR})

# 生成可执行文件
ADD_EXECUTABLE(hello ${SRC_LIST})