# Disable in-source builds to prevent source tree corruption.
if(" ${CMAKE_SOURCE_DIR}" STREQUAL " ${CMAKE_BINARY_DIR}")
  message(FATAL_ERROR "
    FATAL: In-source builds are not allowed.
        You should create a separate directory for build files.
    ")
endif()


cmake_minimum_required(VERSION 3.9 FATAL_ERROR)
project(Crypto LANGUAGES CXX)

# C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Link and include directories
#link_directories( ${GTKMM_LIBRARY_DIRS} )
#include_directories( ${OpenCV_INCLUDE_DIRS} ${GTKMM_INCLUDE_DIRS})

# Testing
include(CTest)
enable_testing()

# Executable
file(GLOB_RECURSE core_cpu_source_files "${CMAKE_SOURCE_DIR}/core/src/*.cpp")
add_executable(${PROJECT_NAME} main.cpp ${core_cpu_source_files})

# Link to libraries
#target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBS} ${GTKMM_LIBRARIES} libuvc.a jpeg usb-1.0)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)