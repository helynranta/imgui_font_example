cmake_minimum_required(VERSION 3.21.2)

project(imgui_example CXX)

find_package(Vulkan REQUIRED)
find_package(sdl2 CONFIG REQUIRED)

set(IMGUI_SOURCES
        imgui/imgui.cpp
        imgui/imgui_demo.cpp
        imgui/imgui_draw.cpp
        imgui/imgui_tables.cpp
        imgui/imgui_widgets.cpp
        imgui/backends/imgui_impl_sdl.cpp
        imgui/backends/imgui_impl_vulkan.cpp
        imgui/examples/example_sdl_vulkan/main.cpp)

add_executable(${PROJECT_NAME} ${IMGUI_SOURCES})

target_include_directories(${PROJECT_NAME} PRIVATE imgui imgui/backends)
target_link_libraries(${PROJECT_NAME} PRIVATE Vulkan::Vulkan SDL2::SDL2 SDL2::SDL2-static)
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_20)
target_compile_definitions(${PROJECT_NAME} PRIVATE IMGUI_VULKAN_DEBUG_REPORT)