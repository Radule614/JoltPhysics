project(JoltPhysics)

# Set C++ version
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Static runtime (for MSVC)
if(MSVC)
    set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
endif()

# Set output directories
set(TARGET_OUTPUT_DIR "${CMAKE_SOURCE_DIR}/bin/${OUTPUT_DIR}/${PROJECT_NAME}")
set(OBJECT_OUTPUT_DIR "${CMAKE_SOURCE_DIR}/bin-int/${OUTPUT_DIR}/${PROJECT_NAME}")

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${TARGET_OUTPUT_DIR})
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${TARGET_OUTPUT_DIR})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${TARGET_OUTPUT_DIR})

# Collect source files
file(GLOB_RECURSE JOLT_SOURCES
        "Jolt/*.cpp"
        "Jolt/*.h"
)

# Define static library
add_library(JoltPhysics STATIC ${JOLT_SOURCES})

# Include directories
target_include_directories(JoltPhysics PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}
)