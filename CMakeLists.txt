# NOTE: This file is only used for configuring CLion, use regular `make` for building.
cmake_minimum_required(VERSION 3.6)
project(esp32_hello_world)

include(environments.txt)

find_program(xtensa-esp32-elf-gcc xtensa-esp32-elf-gcc)
find_program(xtensa-esp32-elf-g++ xtensa-esp32-elf-g++)

set(CMAKE_SYSTEM_NAME xtensa-esp32-elf)
set(CMAKE_C_COMPILER ${xtensa-esp32-elf-gcc})
set(CMAKE_CXX_COMPILER ${xtensa-esp32-elf-g++})

set(CMAKE_FIND_ROOT_PATH ${ESP32_ROOT})

set(CMAKE_CXX_STANDARD 11)

set(COMPONENTS
        app_trace
        app_update
        aws_iot
        bootloader
        bootloader_support
        bt
        coap
        console
        cxx
        driver
        esp-tls
        esp32
        esp_adc_cal
        esp_http_client
        espcoredump
        esptool_py
        ethernet
        expat
        fatfs
        freertos
        heap
        idf_test
        jsmn
        json
        libsodium
        log
        lwip
        mbedtls
        mdns
        micro-ecc
        newlib
        nghttp
        nvs_flash
        openssl
        partition_table
        pthread
        sdmmc
        smartconfig_ack
        soc
        soc/esp32
        spi_flash
        spiffs
        tcpip_adapter
        ulp
        vfs
        wear_levelling
        wpa_supplicant
        xtensa-debug-module)

set(INCLUDE_DIRS "")
foreach (component ${COMPONENTS})
    list(APPEND INCLUDE_DIRS ${IDF_PATH}/components/${component}/include)
endforeach ()
list(REMOVE_DUPLICATES INCLUDE_DIRS)
include_directories(${INCLUDE_DIRS})
include_directories("build/include")

set(SOURCE_FILES
        main/hello_world_main.c
        )
list(APPEND SOURCE_FILES ${SOURCES})

add_executable(${PROJECT_NAME} ${SOURCE_FILES})


