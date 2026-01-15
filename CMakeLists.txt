cmake_minimum_required(VERSION 3.20)
project(SekiroDisableCameraAutoRotate VERSION 0.0.2 LANGUAGES CXX)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Only build for x64
if (NOT CMAKE_SIZEOF_VOID_P EQUAL 8)
    message(FATAL_ERROR "This project only supports 64-bit builds")
endif ()

add_library(SekiroDisableCameraAutoRotate SHARED dllmain.cpp)

# Set output name
set_target_properties(SekiroDisableCameraAutoRotate PROPERTIES
        OUTPUT_NAME "SekiroDisableCameraAutoRotate"
        PREFIX ""
)

# Link required libraries
target_link_libraries(SekiroDisableCameraAutoRotate PRIVATE psapi)

# Windows specific settings
if (WIN32)
    target_compile_definitions(SekiroDisableCameraAutoRotate PRIVATE
            NOMINMAX
    )
endif ()
if (MSVC)
    target_compile_options(SekiroDisableCameraAutoRotate PRIVATE
            /permissive-
            /Zc:__cplusplus
    )
elseif (MINGW)
    target_link_options(SekiroDisableCameraAutoRotate PRIVATE
            -static
            $<$<CONFIG:Release>:-Wl,--strip-all>
    )
endif ()
