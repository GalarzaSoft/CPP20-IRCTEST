cmake_minimum_required(VERSION 3.30.0)

string(REPLACE "\\" "/" VCPKG_ROOT_PATH "$ENV{VCPKG_ROOT}")
set (CMAKE_TOOLCHAIN_FILE  "${VCPKG_ROOT_PATH}/scripts/buildsystems/vcpkg.cmake")#"D:/dev/vcpkg/scripts/buildsystems/vcpkg.cmake")

project(CPP23-IRCTEST)


# Set C++20 standard
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_FIND_ROOT_PATH_MODE_PACKAGE NEVER)

# Find Boost with Asio
find_package(Boost CONFIG REQUIRED COMPONENTS system asio)
find_package(cxxopts CONFIG REQUIRED)

# Add the library project
add_subdirectory(irclibrary)

# Add the server project
add_subdirectory(server)

# Add the client project
add_subdirectory(client)

set_property(DIRECTORY PROPERTY VS_STARTUP_PROJECT client)