cmake_minimum_required( VERSION 3.2 ) 

project( fmt-adapter VERSION 0.0.1 LANGUAGES CXX )

if ( NOT GIT_EXECUTABLE )
    find_package( Git )
    if ( NOT GIT_FOUND )
        message( FATAL_ERROR "git installation was not found." )
    endif()
endif()
execute_process(
    COMMAND ${GIT_EXECUTABLE} rev-parse --abbrev-ref HEAD
    WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}
    OUTPUT_VARIABLE GIT_BRANCH
    OUTPUT_STRIP_TRAILING_WHITESPACE
)
execute_process(
    COMMAND ${GIT_EXECUTABLE} rev-parse HEAD
    WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}
    OUTPUT_VARIABLE GIT_HASH
    OUTPUT_STRIP_TRAILING_WHITESPACE
)

message( STATUS "" )
message( STATUS "-----------------------------------------------------------" )
message( STATUS "" )
message( STATUS "fmt-adapter Version: 0.0.1" )
message( STATUS "Git current branch: ${GIT_BRANCH}" )
message( STATUS "Git commit hash: ${GIT_HASH}" )
message( STATUS "" )
message( STATUS "-----------------------------------------------------------" ) 
message( STATUS "" ) 

add_library( fmt-adapter INTERFACE )
target_sources( fmt-adapter INTERFACE
  "${CMAKE_CURRENT_SOURCE_DIR}/src/fmt/printf.h"
  "${CMAKE_CURRENT_SOURCE_DIR}/src/fmt/format.h"
  "${CMAKE_CURRENT_SOURCE_DIR}/src/fmt/ostream.h"
  "${CMAKE_CURRENT_SOURCE_DIR}/src/fmt/posix.h"
  "${CMAKE_CURRENT_SOURCE_DIR}/src/fmt/string.h"
  "${CMAKE_CURRENT_SOURCE_DIR}/src/fmt/time.h"
  )
target_include_directories( fmt-adapter INTERFACE src/fmt )

