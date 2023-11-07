cmake_minimum_required(VERSION 3.16)
project(imgui)

set(OpenGL_GL_PREFERENCE GLVND)
find_package(OpenGL)
find_package(glfw3)
find_package(FreeGLUT)
set(SOURCES
imgui.cpp
imgui_demo.cpp
imgui_draw.cpp
imgui_tables.cpp
imgui_widgets.cpp
imconfig.h
imgui.h
imgui_internal.h
imstb_rectpack.h
imstb_textedit.h
imstb_truetype.h
)

add_library(${PROJECT_NAME} SHARED ${SOURCES})
target_include_directories(${PROJECT_NAME} PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
)
add_subdirectory(backends)
add_subdirectory(examples)

