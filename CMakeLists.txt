cmake_minimum_required(VERSION 3.2 FATAL_ERROR)
project(event_handler VERSION 0.1 LANGUAGES CXX)

include(GNUInstallDirs)

find_package(Boost 1.63 REQUIRED)
add_library(boost INTERFACE IMPORTED)
set_property(TARGET boost PROPERTY
    INTERFACE_INCLUDE_DIRECTORIES ${Boost_INCLUDE_DIR}
)

enable_testing()
add_subdirectory(src)
add_subdirectory(test)