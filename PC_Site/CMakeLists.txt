cmake_minimum_required(VERSION 3.10)
project(SocketDemo C)

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)



# Compiler warnings

 find_package(PkgConfig REQUIRED)
 pkg_check_modules(LIBAV REQUIRED IMPORTED_TARGET
     libavformat
     libavcodec
     libswresample
     libswscale
     libavutil
 )
 pkg_check_modules(SDL2 REQUIRED IMPORTED_TARGET sdl2)

set(CMAKE_FIND_LIBRARY_SUFFIXES .a ${CMAKE_FIND_LIBRARY_SUFFIXES})

add_compile_options(-Wall -Wextra -Wpedantic)

# UDP live stream receiver + visualizer
add_executable(show_stream show_stream.c)
target_link_libraries(show_stream PUBLIC PkgConfig::LIBAV PkgConfig::SDL2 m)
