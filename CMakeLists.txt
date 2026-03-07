file(GLOB IMGUI_SOURCES
    "*.cpp"
    "*.c"
)

# ImGui header files
file(GLOB IMGUI_HEADERS
    "*.h"
    "*.hpp"
)

# Define ImGui library
add_library(imgui STATIC ${IMGUI_SOURCES} ${IMGUI_HEADERS})

target_include_directories(imgui
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}  # so #include "imgui.h" works
)

# Optional: ImGui backends
target_sources(imgui
    PRIVATE
        backends/imgui_impl_glfw.cpp
        backends/imgui_impl_vulkan.cpp
)

target_include_directories(imgui
    PUBLIC
        backends
)

target_link_libraries(imgui
    PUBLIC
        Vulkan::Vulkan
        glfw
)