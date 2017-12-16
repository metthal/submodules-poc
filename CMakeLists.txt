cmake_minimum_required(VERSION 3.6)
project(Outer CXX)

option(EXTERNAL_INNER "Path to external Inner library." "")

if(NOT EXTERNAL_INNER)
    add_subdirectory(inner)
else()
    add_subdirectory("${EXTERNAL_INNER}" "${CMAKE_CURRENT_BINARY_DIR}/inner")
endif()

add_executable(outer outer.cpp)
target_link_libraries(outer inner)