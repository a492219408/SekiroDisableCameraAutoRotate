cmake_minimum_required(VERSION 3.20)
project(SekiroDisableCameraAutoRotate VERSION 1.0.0)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Only build for x64
if(NOT CMAKE_SIZEOF_VOID_P EQUAL 8)
    message(FATAL_ERROR "This project only supports 64-bit builds")
endif()

add_library(SekiroDisableCameraAutoRotate SHARED dllmain.cpp)

# Set output name
set_target_properties(SekiroDisableCameraAutoRotate PROPERTIES
        OUTPUT_NAME "SekiroDisableCameraAutoRotate"
        PREFIX ""
)

# Link required libraries
target_link_libraries(SekiroDisableCameraAutoRotate PRIVATE psapi)

# Windows specific settings
if(WIN32)
    target_compile_definitions(SekiroDisableCameraAutoRotate PRIVATE
            WIN32_LEAN_AND_MEAN
            NOMINMAX
            _CRT_SECURE_NO_WARNINGS
    )
endif()
if (MINGW)
    target_link_options(SekiroDisableCameraAutoRotate PRIVATE -static-libgcc -static-libstdc++)
endif()
