cmake_minimum_required(VERSION 3.10)
project(lib_name) # lib_name of all header

# Set file list
file(GLOB PROJECT_SRCS
    ${CMAKE_CURRENT_SOURCE_DIR}/*.c
    ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp
    )
# Build library
add_library(${PROJECT_NAME} ${PROJECT_SRCS})

