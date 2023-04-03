if (TARGET tinyusb_device)
    add_executable(ztest
        ztest.c
        )

    # pull in common dependencies
    target_link_libraries(ztest pico_stdlib)

    # enable usb output, disable uart output
    pico_enable_stdio_usb(ztest 1)
    pico_enable_stdio_uart(ztest 0)

    # create map/bin/hex file etc.
    pico_add_extra_outputs(ztest)

    # add url via pico_set_program_url
    example_auto_set_url(ztest)
elseif(PICO_ON_DEVICE)
    message(WARNING "not building hello_usb because TinyUSB submodule is not initialized in the SDK")
endif()