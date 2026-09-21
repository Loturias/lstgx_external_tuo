cmake_minimum_required(VERSION 3.6)

set(lib_name SteamSDK)
set(target_name ext_steam)

project(${lib_name})

if(WINDOWS AND WIN64)
    set(PREBUILT_ROOT ${CMAKE_CURRENT_SOURCE_DIR}/prebuilt_win64)

    add_library(${target_name} SHARED IMPORTED GLOBAL)
    set_target_properties(${target_name} PROPERTIES
        IMPORTED_LOCATION "${PREBUILT_ROOT}/steam_api64.dll"
        IMPORTED_IMPLIB "${PREBUILT_ROOT}/steam_api64.lib"
        INTERFACE_INCLUDE_DIRECTORIES "${CMAKE_CURRENT_SOURCE_DIR}/steam"
    )
else()
    message(FATAL_ERROR "SteamSDK is only available on Windows x64")
endif()

