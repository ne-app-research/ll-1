# SPDX-License-Identifier: Apache-2.0
# Copyright 2026, Amlal El Mahrouss and Ne.app.

cmake_minimum_required(VERSION 3.20)

project(LL_M_Tests
  VERSION 1.0.5
  LANGUAGES CXX
  DESCRIPTION "LL-M formal reasoning ML model tests"
)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_executable(sqrt2_test.o sqrt2.cpp)

target_link_libraries(sqrt2_test.o PUBLIC ll-1.m)

target_include_directories(sqrt2_test.o PUBLIC
  ../kernel/include
  $<$<BOOL:${OCL_INCLUDE_DIR}>:${OCL_INCLUDE_DIR}>
)

target_compile_options(sqrt2_test.o PRIVATE
  $<$<CXX_COMPILER_ID:Clang,GNU>:-Wall -Wextra -Wpedantic>
)
