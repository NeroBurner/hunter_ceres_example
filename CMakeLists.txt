# Copyright (c) 2015, Ruslan Baratov
# All rights reserved.
message(STATUS "CMake Version ${CMAKE_VERSION}")
cmake_minimum_required(VERSION 3.5)


# include HunterGate:
# * https://github.com/hunter-packages/gate
include("cmake/HunterGate.cmake")
HunterGate(
  URL "https://github.com/cpp-pm/hunter/archive/v0.23.237.tar.gz"
  SHA1 "7bf3543bd0e2aecdef07d7e2b743a568b5c3b851"
  LOCAL # cmake/Hunter/config.cmake
)
project(hunter_ceres_example)
# build LAPACK as shared library
#hunter_config(LAPACK
#  VERSION ${HUNTER_LAPACK_VERSION}
#  CMAKE_ARGS BUILD_SHARED_LIBS=ON
#)
# as alternative build LAPACK as static lib by removing the above lines from config.cmake
# If doing so you need to enable Fortran support
# enable_language(Fortran)
# build LAPACK as shared library

hunter_add_package(ceres-solver)

find_package(Ceres CONFIG REQUIRED)

add_executable(foo foo.cpp)
target_link_libraries(foo ceres)

