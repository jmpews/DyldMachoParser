
cmake_minimum_required(VERSION 2.8)
project(DYLDMachoParserProject)

set(CMAKE_CXX_STANDARD 11)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=gnu11")

set(GLOBAL.SOURCE)
set(GLOBAL.SOURCE_DIR)
set(GLOBAL.INCLUDE_DIR)


set(MachoParser.Path dyld3)

list(APPEND MachoParser.SOURCE_DIR
    ${MachoParser.Path}
    ${MachoParser.Path}/shared-cache
)


set(MachoParser.SOURCE_FILE
    ${MachoParser.Path}/MachOParser.cpp
    ${MachoParser.Path}/Diagnostics.cpp
    ${MachoParser.Path}/Logging.cpp
)

set(MachoParser.HEADER_FILE
    ${MachoParser.Path}/MachOParser.h
    ${MachoParser.Path}/Diagnostics.h
    ${MachoParser.Path}/Logging.h
)

set(MachoParser.HEADER_DIR NotFoundFiles)

# ADD_DEFINITIONS(-DDYLD_IN_PROCESS=1)
# ADD_DEFINITIONS(-DTARGET_OS_IOS=1)
include_directories(${MachoParser.SOURCE_DIR} ${MachoParser.HEADER_DIR})

if(BUILD_SHARED)
    add_library(DYLDMachoParser SHARED ${MachoParser.SOURCE_FILE} ${MachoParser.HEADER_FILE})
else()
    add_library(DYLDMachoParser STATIC ${MachoParser.SOURCE_FILE} ${MachoParser.HEADER_FILE})
endif()
target_include_directories(DYLDMachoParser PUBLIC ./)