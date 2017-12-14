cmake_minimum_required(VERSION 2.8.12)

project(cmake_wrapper)
message(WARNING "Conan MySQL Connector/C Wrapped CMake")

include(../conanbuildinfo.cmake)
conan_basic_setup()
include("CMakeListsOriginal.txt")

# Turn off -Werror in GCC debug builds.
if(CMAKE_COMPILER_IS_GNUCC AND CMAKE_COMPILER_IS_GNUCXX)
    target_compile_options(mysys
	PUBLIC -Wno-error)
endif()