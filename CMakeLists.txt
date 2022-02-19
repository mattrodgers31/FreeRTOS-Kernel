cmake_minimum_required(VERSION 3.21)
project(target-freertos LANGUAGES C CXX ASM)

# Suppress warnings for FreeRTOS code
add_compile_options(
    -Wno-conversion
)

add_library(freertos OBJECT
    ${PROJECT_SOURCE_DIR}/croutine.c
    ${PROJECT_SOURCE_DIR}/event_groups.c
    ${PROJECT_SOURCE_DIR}/list.c
    ${PROJECT_SOURCE_DIR}/queue.c
    ${PROJECT_SOURCE_DIR}/stream_buffer.c
    ${PROJECT_SOURCE_DIR}/tasks.c
    ${PROJECT_SOURCE_DIR}/timers.c
    ${PROJECT_SOURCE_DIR}/portable/GCC/ARM_CM4F/port.c
    ${PROJECT_SOURCE_DIR}/portable/MemMang/heap_4.c
)

# Note: may be able to change some of these paths to PRIVATE
target_include_directories(freertos PUBLIC
    ${PROJECT_SOURCE_DIR}/include
    ${PROJECT_SOURCE_DIR}/portable/GCC/ARM_CM4F
)
