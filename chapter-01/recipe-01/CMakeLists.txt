# CMake 版本要求
cmake_minimum_required(VERSION 3.5 FATAL_ERROR)
# 声明项目名称及语言
project(recipe-01 LANGUAGES CXX)
# 指导CMake创建目标程序
add_executable(hello-world hello-world.cpp)
