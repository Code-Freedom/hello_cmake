# 生成可执行文件

# 换个地方存放生成的二进制文件
# 我们都可以通过 SET 指令重新定义 EXECUTABLE_OUTPUT_PATH 和 LIBRARY_OUTPUT_PATH 变量
# 来指定最终的目标二进制的位置(指最终生成的 hello 或者最终的共享库，不包含编译生成
# 的中间文件)
SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
SET(LIBRARY_OUTPUT_PATH  ${PROJECT_BINARY_DIR}/lib)

ADD_EXECUTABLE(hello main.cpp)

INSTALL(PROGRAMS ${PROJECT_BINARY_DIR}/bin/hello DESTINATION bin)