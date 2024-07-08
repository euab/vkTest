cmake_minimum_required(VERSION 3.10)

set(MAIN_FILE
    main.cpp
)

source_group("\\" FILES ${SRC_FILES})

set(SRC
    ${MAIN_FILE}
)

add_executable(${PROJECT_NAME}_exe ${MAIN_FILE})
target_include_directories(${PROJECT_NAME}_exe PUBLIC ${Vulkan_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME}_exe PUBLIC Vulkan::Vulkan)
target_link_libraries(${PROJECT_NAME}_exe PRIVATE glfw)

# Copy glfw3.dll to the output directory
# TODO: NT check
add_custom_command(TARGET ${PROJECT_NAME}_exe POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    $<TARGET_FILE:glfw> $<TARGET_FILE_DIR:${PROJECT_NAME}_exe>)
