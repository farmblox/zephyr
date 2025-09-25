
if(CONFIG_LORA_MODULE_BACKEND_LORA_BASICS_MODEM)
  zephyr_library()
  zephyr_library_sources(
    ${CMAKE_CURRENT_LIST_DIR}/lbm_main_thread.c
  )
endif()
