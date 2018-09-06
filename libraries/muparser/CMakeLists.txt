cmake_minimum_required(VERSION 3.2)
project(muparser)

################ main files ###############

file(GLOB CURRENT_SOURCE_FILES
        ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp
)

file(GLOB CURRENT_HEADER_FILES
        ${CMAKE_CURRENT_SOURCE_DIR}/include/*.h
)

add_library(muparser "${CURRENT_SOURCE_FILES}" "${CURRENT_HEADER_FILES}")

target_include_directories(muparser PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)
