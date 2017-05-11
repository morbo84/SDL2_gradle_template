# stub for a custom project depending on SDL2

cmake_minimum_required(VERSION 3.4.1)

set(PROJECT_DIR my_module)
set(SRC_DIR ${CMAKE_SOURCE_DIR}/${PROJECT_DIR})

# list all source files inside the test dir
file(GLOB_RECURSE SOURCES *.cpp)

# target my_module
set(TARGET_MY_MODULE mysdlproject)
add_library(
    ${TARGET_MY_MODULE}
    SHARED
    ${SOURCES}
    ${SDL2_INCLUDE_DIR}/../src/main/android/SDL_android_main.c
)

# library dependency for the target
target_link_libraries(
        ${TARGET_MY_MODULE}
        PRIVATE ${SDL2_SHARED_LIB_PATH}
)

# include directories for the testall target
target_include_directories(
        ${TARGET_MY_MODULE}
        PRIVATE ${SRC_DIR}
        PRIVATE ${SDL2_INCLUDE_DIR}
)