cmake_minimum_required(VERSION 3.5)

project(Cpp)

set(CMAKE_CXX_FLAGS "-std=c++17 -O3 -fopenmp -march=native -lm")

set(MAIN_HEADERS
    include/main.hpp
    )

set(MAIN_SOURCES
    src/main.cpp
    )

function(build_main)
    add_executable(main ${ECOSYSTEM_SOURCES} ${ECOSYSTEM_HEADERS})
    target_include_directories(ecosystem PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
    target_link_libraries(main)
endfunction()

build_main()
