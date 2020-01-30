cmake_minimum_required(VERSION 3.9.1)

project(CMakeHello)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

message("generated files will be at: ${CMAKE_BINARY_DIR}")

add_executable(cmake_hello main.cpp)

add_subdirectory(lib/math)

find_package(Boost 1.66)

if (Boost_FOUND)
        message("Boost Found")
        include_directories(${Boost_INCLUDE_DIRS})
        target_link_libraries(cmake_hello ${Boost_LIBRARIES})
elseif(NOT Boost_FOUND)
        message(FATAL_ERROR "Boost Not Found")
endif()

target_link_libraries(cmake_hello math)

if(${CMAKE_BUILD_TYPE} MATCHES Debug)
    message("Debug Build")
elseif(${CMAKE_BUILD_TYPE} MATCHES Release)
    message("Release Build")
endif()


