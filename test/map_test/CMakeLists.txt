project(map_test)

add_executable(${PROJECT_NAME} map_test.cpp)

target_include_directories(${PROJECT_NAME}
PUBLIC
${CMAKE_SOURCE_DIR}/src/pnc_map
)

# 链接一下 动态库
target_link_libraries(${PROJECT_NAME}
PUBLIC
pnc_map
)

add_test(
    NAME map_info_test
    COMMAND ${PROJECT_NAME}
)