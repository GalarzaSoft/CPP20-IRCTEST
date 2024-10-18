# server/CMakeLists.txt

# Create the server executable
add_executable(server)

# Add the source files
target_sources(server
    PRIVATE
        src/main.cpp
)

# Link against the irclibrary and Boost libraries
target_link_libraries(server
    PRIVATE
        irclibrary
        Boost::system
        Boost::asio
)

# Specify C++20 module requirements
target_compile_features(server
    PRIVATE
        cxx_std_20
)

# Include Boost headers (no need for library headers, as we use modules)
target_include_directories(server
    PRIVATE
        ${Boost_INCLUDE_DIRS}
)

# Specify output directory for the server executable
set_target_properties(server PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
