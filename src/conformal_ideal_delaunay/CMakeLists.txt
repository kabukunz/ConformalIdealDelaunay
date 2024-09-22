cmake_minimum_required(VERSION 3.16)

set(PROJECT_NAME ConformalIdealDelaunay)
project(${PROJECT_NAME})

list(PREPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
set(DIR_EXT "${CMAKE_CURRENT_SOURCE_DIR}/ext")

set(LIBIGL_INCLUDE_DIR ${DIR_EXT}/libigl/include)
find_package(LIBIGL REQUIRED QUIET)

# binary
set(SOURCE_NAME "CID")
add_executable(${PROJECT_NAME} "${SOURCE_NAME}.cpp")

# target_include_directories(${PROJECT_NAME} "${CMAKE_CURRENT_SOURCE_DIR}/src/util")

target_link_libraries(${PROJECT_NAME} PUBLIC igl::core)

set_target_properties(${PROJECT_NAME} PROPERTIES OUTPUT_NAME ${SOURCE_NAME} RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/bin")

# # added for M_PI definition
# add_compile_definitions(_USE_MATH_DEFINES)
