cmake_minimum_required(VERSION 3.16)

project(MaxiDump)

add_executable(MaxiDump MaxiDump.cpp)
target_link_libraries(MaxiDump PRIVATE dbghelp)

if (MINGW AND CMAKE_CXX_COMPILER_ID MATCHES "Clang")
    target_compile_options(MaxiDump PRIVATE -fms-extensions -g -gcodeview)
    target_link_options(MaxiDump PRIVATE -Wl,--pdb=MaxiDump.pdb)

    add_custom_command(
        TARGET MaxiDump
        POST_BUILD COMMAND ${CMAKE_STRIP} $<TARGET_FILE:MaxiDump>)
endif()

add_custom_target(run COMMAND MaxiDump)
