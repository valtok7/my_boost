cmake_minimum_required(VERSION 3.16.0)
project(my_boost VERSION 0.1.0)

# External Module

## Boost
find_package(Boost REQUIRED COMPONENTS system)
find_package(Threads REQUIRED)
    
## CTest
include(CTest)
enable_testing()

## CPack
set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

# Main
## add executable
add_executable(my_boost src/main.cpp)
target_link_libraries(my_boost PUBLIC Boost::system Threads::Threads)
target_include_directories(my_boost PRIVATE Boost::boost)
set_property(TARGET my_boost PROPERTY CXX_STANDARD 20)
set_property(TARGET my_boost PROPERTY CXX_STANDARD_REQUIRED ON)
set_property(TARGET my_boost PROPERTY CXX_EXTENSION OFF)


