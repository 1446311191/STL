# Copyright (c) Microsoft Corporation.
# SPDX-License-Identifier: Apache-2.0 WITH LLVM-exception

cmake_minimum_required(VERSION 3.22)
project(msvc_standard_libraries_validate LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

add_compile_definitions(NOMINMAX UNICODE _UNICODE)
# we use SAL annotations, so pass /analyze
add_compile_options(/W4 /WX $<$<NOT:$<CONFIG:Debug>>:/Zi> /permissive- /analyze)

add_executable(validate validate.cpp)
