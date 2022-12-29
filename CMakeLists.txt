# CMakeLists.txt
cmake_minimum_required(VERSION 3.0)
project(printnanny-sdwire)

# Find dependencies provided by vcpkg (via vcpkg.cmake)
find_package(libftdi1 CONFIG REQUIRED)
find_package(libpopt CONFIG REQUIRED)

# main target
add_executable(sdwire)
target_sources(sdwire PRIVATE src/main.cpp)
target_link_libraries(sdwire PRIVATE libftdi1::ftdi libpopt::popt)
set_property(TARGET main PROPERTY CXX_STANDARD 17)
