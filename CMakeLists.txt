cmake_minimum_required(VERSION 3.9.1)

project(CMakeHello)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

message("generated files will be at: ${CMAKE_BINARY_DIR}")

add_subdirectory(lib/math)

add_executable(cmake_hello main.cpp)

target_link_libraries(cmake_hello math)

