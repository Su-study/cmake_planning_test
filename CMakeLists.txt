cmake_minimum_required(VERSION 3.20.0)
project(planning
    VERSION 0.0.3
    DESCRIPTION "a demo of cmake planning"
    HOMEPAGE_URL "https://github.com/Su-study/cmake_planning_test"
    LANGUAGES CXX
)
set(CMAKE_CXX_STANDARD 17)

# 设置变量 子目录中也能使用父目录中的变量
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

# 添加子目录
add_subdirectory(src)
