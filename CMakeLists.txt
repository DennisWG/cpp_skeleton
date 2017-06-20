cmake_minimum_required(VERSION 3.2 FATAL_ERROR)
project(cpp_skeleton VERSION 0.1 LANGUAGES CXX)

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

include(GNUInstallDirs)

find_package(Boost 1.63 REQUIRED)
add_library(boost INTERFACE IMPORTED)
set_property(TARGET boost PROPERTY
    INTERFACE_INCLUDE_DIRECTORIES ${Boost_INCLUDE_DIR}
)

enable_testing()
add_subdirectory(src)
add_subdirectory(test)