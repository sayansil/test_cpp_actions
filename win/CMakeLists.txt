cmake_minimum_required(VERSION 3.5)

project(Cpp)

set(CMAKE_CXX_FLAGS "-std=c++17 -O3 -fopenmp -march=native -lm")

set(COOL_HEADERS
    include/cool.hpp
    )

set(COOL_SOURCES
    src/cool.cpp
    )

function(build_cool)
    add_executable(coolok ${COOL_SOURCES} ${COOL_HEADERS})
    target_include_directories(coolok PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
    target_link_libraries(coolok)
endfunction()

build_main()
