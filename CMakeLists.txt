cmake_minimum_required(VERSION 3.20.0)
project(planning)
set(CMAKE_CXX_STANDARD 17)

# 变量和目录设置
# 动态库 和 执行文件 都指定到 bin 目录下面 linux
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)
# 静态库
# CMAKE_ARCHIVE_OUTPUT_DIRECTORY

# 生成动态库
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS)
# 把 src 下 所有的 cpp 文件 生成动态库
add_library(common
SHARED
${SRC_LISTS}
)

# 因为 cpp 文件 依赖头文件，包含头文件
target_include_directories(common
PUBLIC
${PROJECT_SOURCE_DIR}/include
)


set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
# 可执行文件
add_executable(
    planning_main
    planning_main.cpp
)

# cpp 文件同样依赖于 头文件
target_include_directories(planning_main
PUBLIC
${PROJECT_SOURCE_DIR}/include
)

# 链接动态库 可执行文件链接到动态库上
target_link_libraries(planning_main
PUBLIC
common
)