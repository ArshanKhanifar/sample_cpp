cmake_minimum_required(VERSION 3.9.1)

project(CMakeHello)

if(${CMAKE_SYSTEM_NAME} MATCHES Darwin)
        add_definitions(-DCMAKEMACROSAMPLE="Apple MacOS")
elseif(${CMAKE_SYSTEM_NAME} MATCHES Windows)
        add_definitions(-DCMAKEMACROSAMPLE="Windows PC")
elseif(${CMAKE_SYSTEM_NAME} MATCHES Linux)
        add_definitions(-DCMAKEMACROSAMPLE="Linux")
endif()

add_executable(cmake_hello hello.cpp)

