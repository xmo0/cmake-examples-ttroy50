cmake_minimum_required(VERSION 3.5)

# Set the project name
project (third_party_include)

message(STATUS "CMAKE_MODULE_PATH: ${CMAKE_MODULE_PATH}")

message(STATUS "Boost_FOUND: ${Boost_FOUND}")
message(STATUS "Boost_INCLUDE_DIRS: ${Boost_INCLUDE_DIRS}")
# find a boost install with the libraries filesystem and system
find_package(Boost 1.46.1 REQUIRED COMPONENTS filesystem system)
# find_package(Boooooooost 1.46.1 REQUIRED COMPONENTS filesystem system)

# check if boost was found
# Cache variables in FindBoost.cmake
message(STATUS "Boost_FOUND: ${Boost_FOUND}")
message(STATUS "Boost_INCLUDE_DIRS: ${Boost_INCLUDE_DIRS}")
message(STATUS "Boost_LIBRARY_DIRS: ${Boost_LIBRARY_DIRS}")
message(STATUS "Boost_LIBRARIES: ${Boost_LIBRARIES}")
message(STATUS "Boost_SYSTEM_LIBRARY: ${Boost_SYSTEM_LIBRARY}")
message(STATUS "Boost_FILESYSTEM_LIBRARY: ${Boost_FILESYSTEM_LIBRARY}")

if(Boost_FOUND)
    message ("boost found")
else()
    message (FATAL_ERROR "Cannot find Boost")
endif()

# Add an executable
add_executable(third_party_include main.cpp)

# link against the boost libraries
target_link_libraries( third_party_include
    PRIVATE
        Boost::filesystem
)

# Using Dependencies Guide 
# The config file must be named either <PackageName>Config.cmake or <LowercasePackageName>-config.cmake
# (the former is used for the remainder of this guide, but both are supported). 
# This file is the entry point to the package for CMake.
# 
# locate BoostConfig.cmake
# find /lib/ -name "BoostConfig.cmake"
# find /lib/ -name "BoostConfigVersion.cmake"
# /lib/x86_64-linux-gnu/cmake/Boost-1.74.0/BoostConfig.cmake
#
# find /usr/share/cmake-3.22/Modules/ -name 'Find*.cmake' |wc -l
#
