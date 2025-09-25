# SPDX-License-Identifier: Apache-2.0

# LoRa drivers depend on the include directories exposed by the lora_basics_modem
# library. Hence, if it exists then the source files are added to that otherwise
# a library with same name is created.
if(TARGET lora_basics_modem)
  set(ZEPHYR_CURRENT_LIBRARY lora_basics_modem)
else()
  zephyr_library_named(lora_basics_modem)
endif()

# if(CONFIG_LORA_SX126X OR CONFIG_LORA_STM32WL_SUBGHZ_RADIO)
# zephyr_library_sources(lbm_sx126x.c)
# endif()

zephyr_library_sources(lbm_common.c)
zephyr_library_sources_ifdef(CONFIG_LORA_SX127X lbm_sx127x.c)
zephyr_library_sources_ifdef(CONFIG_LORA_RYLRXXX ../rylrxxx.c)
zephyr_library_sources_ifdef(CONFIG_LORA_STM32WL_SUBGHZ_RADIO sx126x_stm32wl.c)

