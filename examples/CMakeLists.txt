cmake_minimum_required(VERSION 3.20)
project(libxc_examples LANGUAGES C CXX Fortran)

find_package(Libxc REQUIRED)

add_executable(cxx_example cxx_example.cpp)
target_link_libraries(cxx_example PRIVATE Libxc::xc)

add_executable(f90_example f90_example.f90)
target_link_libraries(f90_example PRIVATE /usr/local/lib/libxcf03.a Libxc::xc)
