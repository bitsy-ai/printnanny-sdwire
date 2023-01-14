# CMakeLists.txt
cmake_minimum_required(VERSION 3.0)
project(printnanny-sdwire)

# Find dependencies provided by vcpkg (via vcpkg.cmake)
find_path(LIBFTDI1_INCLUDE_DIRS "libftdi1/ftdi.h" REQUIRED)
find_path(LIBPOPT_INCLUDE_DIRS "popt.h" REQUIRED)

message(WARNING "Found FTDI1 includes: ${LIBFTDI1_INCLUDE_DIRS}")
message(WARNING "Found POPT includes: ${LIBPOPT_INCLUDE_DIRS}")

find_library(LIBPOPT popt REQUIRED)
find_library(LIBFTDI1 ftdi1 REQUIRED)
find_library(LIBUSB usb-1.0 REQUIRED)
find_library(LIBCONFUSE libconfuse REQUIRED)

message(WARNING "Found libraries: ${LIBPOPT} ${LIBFTDI1} ${LIBUSB} ${LIBCONFUSE}")

# main target
add_executable(sdwire)
set_property(TARGET sdwire PROPERTY CXX_STANDARD 17)
target_sources(sdwire PRIVATE src/main.cpp)

target_include_directories(sdwire PRIVATE ${LIBFTDI1_INCLUDE_DIRS} ${LIBPOPT_INCLUDE_DIRS})
target_link_libraries(sdwire PRIVATE ${LIBUSB} ${LIBFTDI1} ${LIBCONFUSE} ${LIBPOPT})
