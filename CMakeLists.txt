cmake_minimum_required(VERSION 3.15)
project(detours LANGUAGES CXX)

add_library(detours STATIC
    src/detours.cpp
    src/modules.cpp
    src/disasm.cpp
    src/image.cpp
)

target_include_directories(detours
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)

target_compile_definitions(detours
    PRIVATE
        WIN32_LEAN_AND_MEAN
)

if (MSVC)
    target_compile_options(detours PRIVATE /W3)
endif()

set_target_properties(detours PROPERTIES
    ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib
)
