cmake_minimum_required(VERSION 3.5)

project(Cpp)

set(CMAKE_CXX_FLAGS "-std=c++17 -O3 -march=native -lm -ltbb")
target_compile_features(${TARGET_NAME} PRIVATE cxx_std_17)

set(ECOSYSTEM_HEADERS
    include/nlohmann/json.hpp
    include/prakhar1989/ProgressBar.hpp
    include/helper.hpp
    include/stat_fetcher.hpp
    include/animal.hpp
    include/god.hpp
    include/database_manager.hpp
    include/EcosystemTypes.hpp
    )

set(ECOSYSTEM_SOURCES
    src/helper.cpp
    src/stat_fetcher.cpp
    src/animal.cpp
    src/god.cpp
    src/database_manager.cpp
    )

function(setup_ecosystem)
    add_executable(setup ${CMAKE_CURRENT_SOURCE_DIR}/setup/setup.cpp)
    target_link_libraries(setup PRIVATE sqlite3)
endfunction()

function(build_ecosystem)
    add_executable(ecosystem ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp ${ECOSYSTEM_SOURCES} ${ECOSYSTEM_HEADERS})
    target_include_directories(ecosystem PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
    target_link_libraries(ecosystem sqlite3)
endfunction()

setup_ecosystem()
build_ecosystem()
