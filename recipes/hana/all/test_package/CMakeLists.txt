cmake_minimum_required(VERSION 3.15)
project(test_package)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

find_package(Hana REQUIRED CONFIG)

add_executable(${PROJECT_NAME} test_package.cpp)
target_link_libraries(${PROJECT_NAME} hana)
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 14)
