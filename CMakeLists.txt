# -*- mode: CMAKE; -*-

cmake_minimum_required(VERSION 2.6)

project(linenoise)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release CACHE string "Choose the type of build, options are: None Debug Release RelWithDebInfo MinSizeRel." FORCE)
endif()

message(STATUS "Build mode: ${CMAKE_BUILD_TYPE}")

# INFO
set(LINENOISE_VERSION "1.0.0" CACHE path "Linenoise version")
set(LINENOISE_DISPLAY_NAME "Linenoise-NG")
set(LINENOISE_URL_INFO_ABOUT "https://github.com/arangodb/linenoise-ng")
set(LINENOISE_CONTACT "hackers@arangodb.org")
set(LINENOISE_FRIENDLY_STRING "Linenoise NG - Linenoise Next Generation")

include_directories(${PROJECT_SOURCE_DIR}/include ${PROJECT_SOURCE_DIR}/src)

# build liblinenoise
add_library(
  linenoise
  STATIC
  src/ConvertUTF.cpp
  src/linenoise.cpp
  src/wcwidth.cpp
)

# install
install(TARGETS linenoise DESTINATION lib)

# headers
install(FILES include/linenoise.h DESTINATION include)
