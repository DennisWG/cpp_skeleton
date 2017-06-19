project(cpp_skeleton_test VERSION 0.1 LANGUAGES CXX)

add_executable(test_cpp_skeleton
    dummy.cpp
)

target_link_libraries(test_cpp_skeleton
    lib_cpp_skeleton
)

add_test(test_cpp_skeleton test_cpp_skeleton)