project(cpp_skeleton_test VERSION 0.1 LANGUAGES CXX)

add_executable(test_cpp_skeleton
    dummy.cpp
)

if (CMAKE_BUILD_TYPE STREQUAL "Coverage")
    include(CodeCoverage)
    set_target_properties(
            test_cpp_skeleton PROPERTIES
            COMPILE_FLAGS "-O0 -g -fprofile-arcs -ftest-coverage"
            LINK_FLAGS "-O0 -g -lgcov -fprofile-arcs -ftest-coverage"
    )

    SETUP_TARGET_FOR_COVERAGE(
        coverage
        test_cpp_skeleton
        coverage_report
    )
endif()

target_link_libraries(test_cpp_skeleton
    lib_cpp_skeleton
)

add_test(test_cpp_skeleton test_cpp_skeleton)

install(TARGETS test_cpp_skeleton
    RUNTIME  DESTINATION ${CMAKE_INSTALL_BINDIR}
)

export(TARGETS lib_cpp_skeleton FILE cpp_skeleton_config.cmake)