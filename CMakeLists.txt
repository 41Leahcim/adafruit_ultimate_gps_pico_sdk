cmake_minimum_required(VERSION 3.12)
    
include(pico_sdk_import.cmake)

project(hello_world C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
pico_sdk_init()

add_executable(hello_world
    app.c
    )

# pull in common dependencies
target_link_libraries(hello_world pico_stdlib)

# enable usb output, disable uart output
pico_enable_stdio_usb(hello_world 1)
pico_enable_stdio_uart(hello_world 0)

# create map/bin/hex/uf2 file etc.
pico_add_extra_outputs(hello_world)
