project(imgui_backends)

if(OpenGL_FOUND)

    add_library(imgui_opengl SHARED imgui_impl_opengl3.cpp imgui_impl_opengl3.h imgui_impl_opengl2.cpp imgui_impl_opengl2.h)
    target_link_libraries(imgui_opengl imgui OpenGL::OpenGL)
    target_include_directories(imgui_opengl PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    )

if(glfw3_FOUND)
    add_library(imgui_glfw SHARED imgui_impl_glfw.cpp imgui_impl_glfw.h)
    target_link_libraries(imgui_glfw imgui_opengl glfw)
    target_include_directories(imgui_glfw PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    )
endif()
if(FreeGLUT_FOUND)
    add_library(imgui_glut SHARED imgui_impl_glut.cpp imgui_impl_glut.h)
    target_link_libraries(imgui_glut imgui_opengl FreeGLUT::freeglut)
    target_include_directories(imgui_glut PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    )
endif()
endif()
