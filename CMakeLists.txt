cmake_minimum_required(VERSION 3.0)
project(gtest_min_sample)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

enable_testing()

find_package(Glog)
include_directories(${CMAKE_CURRENT_SOURCE_DIR} googletest/googletest/include)

add_subdirectory(googletest)
add_subdirectory(foo)

# Add test here
add_executable(foo_test_cli foo/foo_test.cc gtest_main.cc)
target_link_libraries(foo_test_cli foo gtest ${GLOG_LIBRARY})
add_test(NAME foo_test COMMAND foo_test_cli)
