cmake_minimum_required(VERSION 3.15)
project(webAssembly C)
##打印编译日志
set(CMAKE_VERBOSE_MAKEFILE ON)
##设置编译器
set(CMAKE_C_COMPILER  /Users/oyo/emsdk/upstream/emscripten/emcc)
MESSAGE(STATUS "CMAKE_C_COMPILER:${CMAKE_C_COMPILER}")
##添加编译器参数
set(CMAKE_C_FLAGS  "-s WASM=1 -O3")
MESSAGE(STATUS "CMAKE_C_FLAGS:${CMAKE_C_FLAGS}")
##包含emscripten头文件
include_directories(/Users/oyo/emsdk/upstream/emscripten/system/include)
##设置生成文件后缀
set(CMAKE_EXECUTABLE_SUFFIX  ".js")
##生成目标文件
add_executable(webAssembly src/main.c)
##当前二进制文件目录
MESSAGE(STATUS "CMAKE_CURRENT_BINARY_DIR:${CMAKE_CURRENT_BINARY_DIR}")
##当前源码文件目录
MESSAGE(STATUS "CMAKE_CURRENT_SOURCE_DIR:${CMAKE_CURRENT_SOURCE_DIR}")
##将编译文件放到目标路径下
install (FILES
        ${CMAKE_CURRENT_BINARY_DIR}/webAssembly.js
        ${CMAKE_CURRENT_BINARY_DIR}/webAssembly.wasm
        DESTINATION ${CMAKE_CURRENT_SOURCE_DIR}/root)
