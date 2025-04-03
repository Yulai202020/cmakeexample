cmake_minimum_required(VERSION 3.12.4)

project(example) # set project name

set(CMAKE_C_COMPILER musl-gcc)

add_executable(${PROJECT_NAME} main.c) # make executable
set_target_properties(${PROJECT_NAME} PROPERTIES LINK_FLAGS "-static")

add_library(mylib STATIC mylib.c) # make library
target_link_libraries(${PROJECT_NAME} SHARED mylib) # link libs

# $ENV{PATH} get from enviremont
# $VAR_NAME get from cache or local

# set(VAR_NAME VALUE) - create var
# set(VAR_NAME VALUE1 VALUE2 VALUE3) - create list
# set(VAR_NAME VALUE CACHE TYPE "<description>" [FORCE]) - create var in cmake cache
# option(VAR_NAME "<description>" VALUE) - create boolean var
# unset(VAR_NAME [CACHE]) delete variable
# math(expression) - get result of math expression

# list() - perform manipulation on a list
# list(APPEND MY_LIST ITEM1 ITEM2) - append to list
# list(INSERT MY_LIST 0 item0) - insert item0 to first position
# list(LENGTH MY_LIST LIST_SIZE) - write length of my_list to var list_size
# list(GET MY_LIST 1 MY_ITEM) - write second item to var my_item
# list(REMOVE_AT MY_LIST 1) - remove second item

# string() - perform manipulation on a string
# string(APPEND my_str " World!") - append to end
# string(ASCII 65 my_char) - number to char
# string(CONFIGURE "Hello, ${var}!" my_result) - sprintf
# string(CONCAT my_str "Hello" " " "CMake" "!") - make sum of strings
# string(FIND "Hello CMake" "CMake" pos) - find
# string(FORMAT my_str "Value: %d, Hex: %X" 42 42) - format (printf)
# string(JOIN ", " my_str ${my_list}) - join list by ", " and write to my_str
# string(LENGTH "Hello" STR_SIZE) - get length and write to var STR_SIZE
# string(REPEAT "Ha" 3 my_str) - repeat 3 time "Ha" and write to my_str
# string(SUBSTRING "Hello CMake" 6 5 my_sub) - cut substring
# string(TOLOWER "Hello CMake!" my_str) - to lower
# string(TOUPPER "Hello CMake!" my_str) - to upper

# project(PROJECT_NAME)
# message([STATUS|WARNING|AUTHOR_WARNING|SEND_ERROR|FATAL_ERROR|DEPRECATION] text) - say message
# add_executable(OUTPUT_FILE SOURCE_FILE) # make executable
# add_library(LIB_NAME [SHARED|STATIC] HEADER_FILE SOURCE_FILE)
# add_subdirectory(DIR) adds subs dir but in sub dir cloud be CMakeLists.txt

# find_program(path_to_program program [PATHS...]) - write path to program to path_to_program
# find_library(path_to_lib NAMES mylib [PATHS...])
# find_file()
# find_path(VAR_NAME file_name [PATHS...])
# find_file(VAR_NAME file_name [PATHS...])


# if(condition)
# elseif(condition)
# else()
# endif()

# function(FUNC_NAME) - create function
# return()
# endfunction()

# FUNC_NAME() - run function

# while(condition)
# endwhile()

# foreach(<loop_var> <items>)
# endforeach()

# foreach(ITEM IN LISTS MY_LIST) - foreach by list
#     message("Item: ${ITEM}")
# endforeach()

# foreach(ITEM RANGE START END) - foreach by range
# endforeach()

# break()
# continue()

# set c++ standart requirements

# set(CMAKE_C_COMPILER musl-gcc) - use another compiler
# set(CMAKE_CXX_COMPILER g++) - use another compiler

# set(CMAKE_CXX_STANDARD 11) - change c++ standart
# set(CMAKE_CXX_STANDARD_REQUIRED True) - using standart is required

# set(BINARY_DIR "${CMAKE_BINARY_DIR}")
# set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${BINARY_DIR}/bin")
# set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${BINARY_DIR}/lib")
# set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${BINARY_DIR}/lib")