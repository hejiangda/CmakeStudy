# set minimum cmake version
cmake_minimum_required(VERSION 3.5 FATAL_ERROR)

# project name and language
project(recipe-03 LANGUAGES CXX)

# generate a library from sources
# 生成静态库 注意add_library 的第二个参数
add_library(message
  STATIC
    Message.hpp
    Message.cpp
  )
# 生成可执行文件
add_executable(hello-world hello-world.cpp)
# 链接message库
target_link_libraries(hello-world message)
