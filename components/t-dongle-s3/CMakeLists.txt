# only register the component if the target is esp32s3
idf_component_register(
  INCLUDE_DIRS "include"
  SRC_DIRS "src"
  REQUIRES driver fatfs base_component display display_drivers i2c interrupt led_strip task
  REQUIRED_IDF_TARGETS "esp32s3"
  )
