# Generated CMake Pico project file

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# == DO NOT EDIT THE FOLLOWING LINES for the Raspberry Pi Pico VS Code Extension to work ==
if(WIN32)
    set(USERHOME $ENV{USERPROFILE})
else()
    set(USERHOME $ENV{HOME})
endif()
set(sdkVersion 2.1.0)
set(toolchainVersion 13_3_Rel1)
set(picotoolVersion 2.1.0)
set(picoVscode ${USERHOME}/.pico-sdk/cmake/pico-vscode.cmake)
if (EXISTS ${picoVscode})
    include(${picoVscode})
endif()
# ====================================================================================

set(PICO_BOARD pico_w CACHE STRING "Board type")

# Pull in Raspberry Pi Pico SDK (must be before project)
include(pico_sdk_import.cmake)

# Nome do projeto
project(Tarefa_conversorAD C CXX ASM)

# Inicializa o SDK da Raspberry Pi Pico
pico_sdk_init()

# Adiciona o executável principal
add_executable(Tarefa_conversorAD 
    Tarefa_conversorAD.c 
    inc/ssd1306.c   # Adiciona a implementação do display SSD1306
)

# Define o nome e a versão do programa
pico_set_program_name(Tarefa_conversorAD "Tarefa_conversorAD")
pico_set_program_version(Tarefa_conversorAD "0.1")

# Ativa saída via USB e desativa UART
pico_enable_stdio_uart(Tarefa_conversorAD 0)
pico_enable_stdio_usb(Tarefa_conversorAD 1)

# Adiciona as bibliotecas do Pico necessárias para o projeto
target_link_libraries(Tarefa_conversorAD 
    pico_stdlib 
    hardware_adc  # Biblioteca para leitura de ADC
    hardware_pwm  # Biblioteca para controle de PWM
    hardware_i2c  # Biblioteca para comunicação I2C (Display SSD1306)
)

# Adiciona os diretórios de inclusão
target_include_directories(Tarefa_conversorAD PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}   # Inclui a pasta principal
    ${CMAKE_CURRENT_LIST_DIR}/inc  # Inclui a pasta inc (onde os headers ssd1306.h e font.h estão)
)

# Adiciona os arquivos de saída
pico_add_extra_outputs(Tarefa_conversorAD)
