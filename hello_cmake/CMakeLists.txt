project(HELLO_CMAKE)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)

add_executable(hello main.cpp hello.cpp)

install(TARGETS hello DESTINATION bin)
install(FILES hello.h DESTINATION include)
install(DIRECTORY ${PROJECT_SOURCE_DIR} DESTINATION src)