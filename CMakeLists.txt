cmake_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)
project(practica_wokwi C CXX ASM)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

pico_sdk_init()

add_executable(practica_wokwi
  src/main.cpp
)

# NOTE:
# The firmware uses Arduino-style APIs (Keypad, pinMode, digitalWrite, delay).
# Build this source with an Arduino-compatible RP2040 core, or adapt with wrappers
# if compiling directly against Pico SDK.

target_link_libraries(practica_wokwi pico_stdlib)

pico_add_extra_outputs(practica_wokwi)
