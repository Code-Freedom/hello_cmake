# PROJECT(projectname, [CXX] [C] [Java])
# 隐含定义了两个变量 <projectname>_SOURCE_DIR 和 <projectname>_BINARY_DIR
# 通常情况下，值与 PROJECT_SOURCE_DIR 和 PROJECT_BINARY_DIR 相同
PROJECT(HELLO)

# ADD_SUBDIRECTORY(source_dir [binary_dir] [EXCLUDE_FROM_ALL])
# 用来想当前工程添加存放源文件的子目录，并可以指定中间二进制文件和目标二进制文件的存放位置。
# [EXECLUDE_FROM_ALL] 参数将这个目录从编译过程中排除，比如，工程的 example。
# 一个可能的用法便是，等待工程编译完了在进入 example 文件夹编译样例
ADD_SUBDIRECTORY(src bin)


# INSTALL 设置如何安装这个工程
# 安装一般的文件（版权文件、说明文件等）
INSTALL(FILES COPYRIGHT README DESTINATION share/doc/hellocmake/better_hello_world)

INSTALL(PROGRAMS hellocmake.sh DESTINATION bin)

# 演示安装 doc 文件
INSTALL(DIRECTORY doc/ DESTINATION share/doc/hellocmake/better_hello_world)

# 演示如何使用 CPack 打包成 deb

# 包名
set(CPACK_PACKAGE_NAME "test-pkg-name")

set(CPACK_SET_DESTDIR ON)

# 安装路径前缀
set(CPACK_INSTALL_PREFIX "/home/chaoqun/test")

# 包版本
set(CPACK_PACKAGE_VERSION "0.0.1")

# 设置 group 名字                                     
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "codefreedom")      

# 设置 vendor 名字                             
set(CPACK_PACKAGE_VENDOR "chaoqun")    

# 设置 license 信息                                  
set(CPACK_RPM_PACKAGE_LICENSE "Apache 2.0 + Common Clause 1.0")
include(CPack)

