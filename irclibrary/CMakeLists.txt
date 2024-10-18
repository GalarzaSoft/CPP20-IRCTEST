# library/CMakeLists.txt

# Create the shared library
add_library(irclibrary STATIC src/library.cppm)

# Add the source files
target_sources(irclibrary
    PRIVATE
        src/library.cppm  # Add your source files here
)

# Include the headers directory
#target_include_directories(irclibrary
#    PUBLIC
#        ${CMAKE_CURRENT_SOURCE_DIR}/headers
#)

# Specify C++20 module requirements
target_compile_features(irclibrary
    PUBLIC
        cxx_std_20
)

# Specify output directory for the shared library
set_target_properties(irclibrary PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
    LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib
    ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib
)
