cmake_minimum_required(VERSION 3.16)

project(ConformalSeamlessSimilarity)

list(PREPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
set(DIR_EXT "${CMAKE_CURRENT_SOURCE_DIR}/ext")

include_directories("${CMAKE_CURRENT_SOURCE_DIR}/src/util")

set(LIBIGL_INCLUDE_DIR ${DIR_EXT}/libigl/include)
find_package(LIBIGL REQUIRED QUIET)

# binary
add_executable(CSM_bin src/conformal_seamless_similarity/CSM.cpp)
target_link_libraries(CSM_bin PUBLIC igl::core)

# added for M_PI definition
add_compile_definitions(_USE_MATH_DEFINES)
