cmake_minimum_required(VERSION 3.15)
project(test_package LANGUAGES CXX)

find_package(Drogon CONFIG REQUIRED)

add_executable(${PROJECT_NAME} test_package.cpp)
target_link_libraries(${PROJECT_NAME} PRIVATE Drogon::Drogon)

# drogon uses string_view when MSVC_VERSION is greater than 1900.
# https://github.com/drogonframework/drogon/blob/v1.7.5/lib/inc/drogon/utils/string_view.h#L16
if((DEFINED MSVC_VERSION AND MSVC_VERSION GREATER 1900) OR Drogon_VERSION VERSION_GREATER_EQUAL "1.8.2")
    target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_17)
else()
    target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_14)
endif()
