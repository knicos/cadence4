cmake_minimum_required (VERSION 2.6)
project (cadence4)

# Need to include staged files and libs
include_directories(${PROJECT_SOURCE_DIR}/include)
include_directories(${PROJECT_BINARY_DIR})

set(dsb_VERSION_MAJOR "4")
set(dsb_VERSION_MINOR "1")
set(dsb_VERSION_PATCH "1")

option(WITH_NO_THREADS "Disable multi-threading" OFF)

set(CMAKE_C_FLAGS "-Wall -Werror")
set(CMAKE_C_FLAGS_DEBUG "-D_DEBUG -g -Wall -Werror")
set(CMAKE_C_FLAGS_RELEASE "-O3")

set(CADENCESOURCE source/main.c)

configure_file( ${CMAKE_SOURCE_DIR}/include/cadence4/config.h.in ${CMAKE_BINARY_DIR}/cadence4/config.h )

add_executable(cad4 ${CADENCESOURCE})
target_link_libraries(cad4 dl)

install(PROGRAMS "${PROJECT_BINARY_DIR}/cad4" DESTINATION bin)

