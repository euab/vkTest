cmake_minimum_required(VERSION 3.16)

find_package(Vulkan)

# globally define debug mode when building in debug
add_compile_definitions($<$<CONFIG:DEBUG>:DEBUG_MODE>)

project(
  vkTest
  VERSION ${PROJECT_VERSION}
  DESCRIPTION "Vulkan Test Application"
  LANGUAGES CXX
)

file(MAKE_DIRECTORY output)

add_subdirectory(third_party)

add_subdirectory(src)
