cmake_minimum_required(VERSION 2.8.11)

project(gpp C)

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

set(gpp_VERSION_MAJOR 2)
set(gpp_VERSION_MINOR 25)
set(gpp_VERSION "${gpp_VERSION_MAJOR}.${gpp_VERSION_MINOR}")

set(PACKAGE           "gpp")
string(TOUPPER ${PACKAGE} PACKAGE_UPPER)

set(PACKAGE_VERSION   "${gpp_VERSION}")
set(PACKAGE_BUGREPORT "http://en.nothingisreal.com/wiki/GPP")
set(PACKAGE_NAME      "${PACKAGE_UPPER}")
set(PACKAGE_STRING    "${PACKAGE_UPPER} ${PACKAGE_VERSION}")
set(PACKAGE_TARNAME   "${PACKAGE}")
set(PACKAGE_URL       "http://en.nothingisreal.com/wiki/GPP")

include (CheckIncludeFiles)
include (CheckFunctionExists)

check_include_files(fnmatch.h HAVE_FNMATCH_H)
check_include_files(inttypes.h HAVE_INTTYPES_H)
check_include_files(memory.h HAVE_MEMORY_H)
check_include_files(stdint.h HAVE_STDINT_H)
check_include_files(stdlib.h HAVE_STDLIB_H)
check_include_files(strings.h HAVE_STRINGS_H)
check_include_files(string.h HAVE_STRING_H)
check_include_files(sys/stat.h HAVE_SYS_STAT_H)
check_include_files(sys/types.h HAVE_SYS_TYPES_H)
check_include_files(unistd.h HAVE_UNISTD_H)

check_function_exists(strcasecmp HAVE_STRCASECMP)
check_function_exists(strchr HAVE_STRCHR)
check_function_exists(strdup HAVE_STRDUP)
check_function_exists(strtol HAVE_STRTOL)

include(CheckSymbolExists)
check_symbol_exists(size_t "sys/types.h" HAVE_SIZE_T)

include (CheckCCompiler)
include (CheckStdCHeaders)
check_c_compiler_supports_const(HAVE_C_CONST)
check_c_compiler_supports_inline(INLINE HAVE_C_INLINE)

include(CheckStdCHeaders)

configure_file(
  ${CMAKE_CURRENT_SOURCE_DIR}/config.h.in
  ${CMAKE_CURRENT_BINARY_DIR}/config.h)

include_directories(${CMAKE_CURRENT_BINARY_DIR})

add_definitions(-DHAVE_CONFIG_H)

add_subdirectory(src)
