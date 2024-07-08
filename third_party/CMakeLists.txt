cmake_minimum_required(VERSION 3.10)

project(third_party LANGUAGES C CXX)

option(GLFW_BUILD_DOCS OFF)
option(GLFW_BUILD_TESTS OFF)
option(GLFW_BUILD_EXAMPLES OFF)
option(GLFW_BUILD_TESTS OFF)
option(GLFW_INSTALL OFF)
option(BUILD_SHARED_LIBS ON)

add_subdirectory(glfw)

if (TARGET update_mappings)
    set_target_properties(update_mappings PROPERTIES FOLDER "ThirdParty")
endif()
set_property(TARGET glfw PROPERTY FOLDER "ThirdParty")
