cmake_minimum_required(VERSION 3.20)

project(ThreeFingerDrag LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_executable(ThreeFingerDrag WIN32
    ThreeFingerDrag/ThreeFingerDrag.cpp
    ThreeFingerDrag/config/globalconfig.cpp
    ThreeFingerDrag/logging/logger.cpp
    ThreeFingerDrag/mouse/cursor.cpp
    ThreeFingerDrag/notification/popups.cpp
    ThreeFingerDrag/notification/wintoastlib.cpp
    ThreeFingerDrag/gesture/touch_processor.cpp
    ThreeFingerDrag/ThreeFingerDrag.rc
)

target_include_directories(ThreeFingerDrag PRIVATE
    ThreeFingerDrag
)

target_compile_definitions(ThreeFingerDrag PRIVATE
    UNICODE
    _UNICODE
    _WIN32_WINNT=0x0A00
    NTDDI_VERSION=0x0A000000
)

target_link_libraries(ThreeFingerDrag PRIVATE
    advapi32
    comctl32
    gdi32
    hid
    ole32
    oleaut32
    psapi
    runtimeobject
    shell32
    shlwapi
    taskschd
    user32
    windowsapp
)

set_target_properties(ThreeFingerDrag PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/build"
)