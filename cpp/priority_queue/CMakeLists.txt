cmake_minimum_required(VERSION 3.16)
project(priority_queue VERSION 0.0 DESCRIPTION "Priority Queue")

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_POLICY_DEFAULT_CMP0077 NEW)

include(FetchContent)

enable_testing()

FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/refs/tags/release-1.11.0.zip
)

FetchContent_MakeAvailable(googletest)

include(GoogleTest)

add_executable(
	${PROJECT_NAME}_test
	src/${PROJECT_NAME}/${PROJECT_NAME}_test.cpp
)

target_include_directories(${PROJECT_NAME}_test PRIVATE include)
target_link_libraries(
	${PROJECT_NAME}_test
	gtest_main
)

gtest_discover_tests(${PROJECT_NAME}_test)
