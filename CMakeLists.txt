# Integrate this with your CMake

pico_generate_pio_header(project ${CMAKE_CURRENT_LIST_DIR}/pio/joybus.pio)

add_custom_command(OUTPUT ${CMAKE_CURRENT_LIST_DIR}/generated/joybus.pio.h
        DEPENDS ${CMAKE_CURRENT_LIST_DIR}/joybus.pio
        COMMAND Pioasm ${CMAKE_CURRENT_LIST_DIR}/joybus.pio ${CMAKE_CURRENT_LIST_DIR}/generated/joybus.pio.h
        )

target_link_libraries(project pico_stdlib pico_platform hardware_pio)
