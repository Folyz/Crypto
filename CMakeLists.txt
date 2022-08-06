# Disable in-source builds to prevent source tree corruption.
if(" ${CMAKE_SOURCE_DIR}" STREQUAL " ${CMAKE_BINARY_DIR}")
  message(FATAL_ERROR "
    FATAL: In-source builds are not allowed.
        You should create a separate directory for build files.
    ")
endif()

cmake_minimum_required(VERSION 3.9 FATAL_ERROR)
project(Crypto)

add_subdirectory(application)