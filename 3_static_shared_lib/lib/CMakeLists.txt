set(HELLOLIB_SRC hello.cpp)

# 更改保存路径
set(LIBRARY_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/lib)

# ADD_LIBRARY(libname [SHARED|STATIC|MODULE] [EXCLUDE_FROM_ALL] source1 source2 ... sourceN)
# add_library 支持三种类型 SHARED 动态库 STATIC 静态库 MODULE 对于支持dyld的系统有效

# 动态库
add_library(hellolib SHARED ${HELLOLIB_SRC})
# 为了能够同时生成 .so 和 .a 文件，修改 CLEAN_DIRECT_OUTPUT 属性
set_target_properties( hellolib PROPERTIES CLEAN_DIRECT_OUTPUT 1)
# 修改版本号属性
SET_TARGET_PROPERTIES(hellolib PROPERTIES VERSION 1.1 SOVERSION 1)

# 静态库
# add_library(hellolib STATIC ${HELLOLIB_SRC})
# 此时因为目标名相同，无法同时生成两者
add_library(hellolib_static STATIC ${HELLOLIB_SRC})
# set_target_properties 可以配置输出的属性
set_target_properties( hellolib_static PROPERTIES OUTPUT_NAME "hellolib")
set_target_properties( hellolib_static PROPERTIES CLEAN_DIRECT_OUTPUT 1)


# install
install (FILES hello.h DESTINATION include/hello)
install(TARGETS hellolib hellolib_static 
    LIBRARY DESTINATION lib 
    ARCHIVE DESTINATION lib)