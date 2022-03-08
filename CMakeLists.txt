# This CMake file doesn't include tests or benchmarks. This is purely just for linking against argon2.

cmake_minimum_required(VERSION 3.0)
project(argon2 DESCRIPTION "Argon2 reference source code package - reference C implementations" VERSION 0)

find_package(Threads REQUIRED)

set(SRC 
  src/argon2.c 
  src/core.c 
  src/blake2/blake2b.c 
  src/thread.c 
  src/encoding.c
  src/opt.c) # opt.c is optimized version of ref.c

add_library(${PROJECT_NAME} STATIC ${SRC})
target_include_directories(${PROJECT_NAME} PUBLIC src include)
target_link_libraries(${PROJECT_NAME} Threads::Threads)
