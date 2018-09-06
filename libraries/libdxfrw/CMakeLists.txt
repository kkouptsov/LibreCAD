cmake_minimum_required(VERSION 3.2)
project(libdxfrw)

################ main files ###############

file(GLOB CURRENT_SOURCE_FILES
        ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp
        ${CMAKE_CURRENT_SOURCE_DIR}/src/intern/*.cpp
)

file(GLOB CURRENT_HEADER_FILES
        ${CMAKE_CURRENT_SOURCE_DIR}/src/*.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/intern/*.h
)

add_library(libdxfrw "${CURRENT_SOURCE_FILES}" "${CURRENT_HEADER_FILES}")

target_include_directories(libdxfrw PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/include
        ${CMAKE_CURRENT_SOURCE_DIR}/include/intern
)
