cmake_minimum_required(VERSION 3.5)

project(VVVCool)

set(CMAKE_CXX_FLAGS "-std=c++17 -O3 -fopenmp -march=native -lm")

function(build_cool)
    add_executable(coolok cool.cpp)
endfunction()

build_cool()
