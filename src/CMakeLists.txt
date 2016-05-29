
if (WIN32)
  add_definitions(-DWIN_NT)
  add_definitions(-D_CRT_SECURE_NO_WARNINGS)
  add_definitions(-D_CRT_SECURE_NO_DEPRECATE -D_CRT_NONSTDC_NO_DEPRECATE)
endif()

add_executable(gpp gpp.c)
