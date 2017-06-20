project(cpp_skeleton_lib VERSION 0.1 LANGUAGES CXX)

add_library(lib_cpp_skeleton
	dummy.cpp
)

target_include_directories(lib_cpp_skeleton
    PUBLIC
	    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/../include>
	    $<INSTALL_INTERFACE:../include>
)

target_compile_features(lib_cpp_skeleton
    PUBLIC cxx_std_17
)

target_link_libraries(lib_cpp_skeleton
    boost
)

install(TARGETS lib_cpp_skeleton EXPORT cpp_skeleton_config
    ARCHIVE  DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY  DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME  DESTINATION ${CMAKE_INSTALL_BINDIR}
)
install(DIRECTORY ../include/ DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})

install(EXPORT cpp_skeleton_config DESTINATION share/MyLibrary/cmake)

export(TARGETS lib_cpp_skeleton FILE cpp_skeleton_config.cmake)

if (CMAKE_BUILD_TYPE STREQUAL "Coverage")
    include(CodeCoverage)
    setup_target_for_coverage(cpp_skeleton_coverage lib_cpp_skeleton coverage)

    SET(CMAKE_CXX_FLAGS "-g -O0 -fprofile-arcs -ftest-coverage")
    SET(CMAKE_C_FLAGS "-g -O0 -fprofile-arcs -ftest-coverage")
endif()