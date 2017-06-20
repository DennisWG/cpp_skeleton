project(cpp_skeleton_test VERSION 0.1 LANGUAGES CXX)

add_executable(test_cpp_skeleton
    dummy.cpp
)

target_link_libraries(test_cpp_skeleton
    lib_cpp_skeleton
)

add_test(test_cpp_skeleton test_cpp_skeleton)

install(TARGETS test_cpp_skeleton
    RUNTIME  DESTINATION ${CMAKE_INSTALL_BINDIR}
)

if (CMAKE_BUILD_TYPE STREQUAL "Coverage")
    #include(CodeCoverage)
    #setup_target_for_coverage(cpp_skeleton_coverage test_cpp_skeleton)

    SET(CMAKE_CXX_FLAGS "-g -O0 -fprofile-arcs -ftest-coverage")
    SET(CMAKE_C_FLAGS   "-g -O0 -fprofile-arcs -ftest-coverage")
#    set_target_properties(test_cpp_skeleton PROPERTIES
#        COMPILE_FLAGS "-g -O0 -fprofile-arcs -ftest-coverage"
#    )
endif()

export(TARGETS lib_cpp_skeleton FILE cpp_skeleton_config.cmake)