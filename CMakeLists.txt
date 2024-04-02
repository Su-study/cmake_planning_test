cmake_minimum_required(VERSION 3.20.0)
project(planning
    VERSION 0.0.3
    DESCRIPTION "a demo of cmake planning"
    HOMEPAGE_URL "https://github.com/Su-study/cmake_planning_test"
    LANGUAGES CXX
)
set(CMAKE_CXX_STANDARD 17)
enable_testing()

# 设置变量 子目录中也能使用父目录中的变量
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)


# 第三方库
set(EIGEN3_INCLUDE_DIR ${CMAKE_SOURCE_DIR}/third_party/eigen)
list(APPEND CMAKE_MODULE_PATH "${EIGEN3_INCLUDE_DIR}/camke")
message("CMAKE_MODULE_PATH = ${CMAKE_MODULE_PATH}")

find_package(Eigen3 3.4 REQUIRED)
if(TARGET Eigen3::Eigen)
    message(STATUS "*********  Eigen3 3.4 found in ${EIGEN3_INCLUDE_DIR} ************")
endif()


# 添加子目录
add_subdirectory(src)
add_subdirectory(test/map_test)


