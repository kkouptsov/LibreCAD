project(ttf2lff)
cmake_minimum_required(VERSION 3.2)

################ FreeType ###############

mark_as_advanced(FREETYPE_INCLUDE_DIR)
find_path(FREETYPE_INCLUDE_DIR
        NAMES ft2build.h
        PATHS ${FREETYPE_LOCATION_DIR}/include ${FREETYPE_LOCATION_DIR}
        NO_DEFAULT_PATH
)

message(STATUS ${FREETYPE_INCLUDE_DIR})

if(${FREETYPE_INCLUDE_DIR} STREQUAL FREETYPE_INCLUDE_DIR-NOTFOUND) 
        message(FATAL_ERROR "FreeType include directory not found") 
endif()

mark_as_advanced(FREETYPE_LIBRARY_DIR)
find_library(FREETYPE_LIBRARY_DIR
        NAMES freetype
        PATHS ${FREETYPE_LOCATION_DIR} ${FREETYPE_LOCATION_DIR}/win64
        NO_DEFAULT_PATH
)

if(${FREETYPE_LIBRARY_DIR} STREQUAL FREETYPE_LIBRARY_DIR-NOTFOUND) 
        message(FATAL_ERROR "FreeType library not found") 
endif()

################ main files ###############

file(GLOB CURRENT_SOURCE_FILES
        ${CMAKE_CURRENT_SOURCE_DIR}/ttf2lff/*.cpp
)

file(GLOB CURRENT_HEADER_FILES
        ${CMAKE_CURRENT_SOURCE_DIR}/ttf2lff/*.h
)

add_executable(ttf2lff "${CURRENT_SOURCE_FILES}" "${CURRENT_HEADER_FILES}")

target_include_directories(ttf2lff PRIVATE
        ${FREETYPE_INCLUDE_DIR}
)
