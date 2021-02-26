cmake_minimum_required(VERSION 3.0.0)
project(Shaper VERSION 0.1.0)

include(CTest)
enable_testing()

add_library("glad" "${CMAKE_SOURCE_DIR}/deps/glad/src/glad.c")

include_directories(
    "${CMAKE_SOURCE_DIR}/deps/glad/include"
    )


add_executable(Shaper main.cpp)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
