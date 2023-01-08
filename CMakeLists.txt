cmake_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)

project(main)

pico_sdk_init()

add_compile_options(
	-Wall
	-Wno-format
	-Wno-unused-function
	-Wno-maybe-uninitialized
	-Wextra    			# optional
	)

add_executable(main)

pico_generate_pio_header(main ${CMAKE_CURRENT_LIST_DIR}/squarewave.pio)

target_sources(main PRIVATE main.c)

target_link_libraries(main pico_stdlib hardware_pio)

# pico_enable_stdio_usb(main 1)
pico_enable_stdio_uart(main 1)

pico_add_extra_outputs(main)
