# set minimum cmake version
cmake_minimum_required(VERSION 3.5 FATAL_ERROR)

# project name and language
project(recipe-03 LANGUAGES CXX)

# generate an object library from sources
# 生成对象库，当需要同时生成静态库和动态库时需要用到
add_library(message-objs
  OBJECT
    Message.hpp
    Message.cpp
  )

# this is only needed for older compilers
# but doesn't hurt either to have it
# 旧版编译器需要用到
set_target_properties(message-objs
  PROPERTIES
    POSITION_INDEPENDENT_CODE 1
  )
# 生成动态库，注意第三个参数的写法
add_library(message-shared
  SHARED
    $<TARGET_OBJECTS:message-objs>
  )
# 设置动态库输出名
set_target_properties(message-shared
  PROPERTIES
    OUTPUT_NAME "message"
  )
# 生成静态库，注意第三个参数的写法
add_library(message-static
  STATIC
    $<TARGET_OBJECTS:message-objs>
  )
# 设置静态库输出名
set_target_properties(message-static
  PROPERTIES
    OUTPUT_NAME "message"
  )
# 生成可执行文件
add_executable(hello-world hello-world.cpp)
# 链接静态库到hello-world
target_link_libraries(hello-world message-static)
