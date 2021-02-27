cmake_minimum_required(VERSION 3.0.0)
project(Shaper VERSION 0.1.0)

find_package(OpenGL REQUIRED)

find_library(GLFW glfw3 PATHS "${CMAKE_SOURCE_DIR}/deps/glfw-3.3.2.bin.WIN64/lib-mingw-w64")

# Windows paths would also just work like c:/users/matth/devel/...
add_library("glad" "${CMAKE_SOURCE_DIR}/deps/glad/src/glad.c")

include_directories(
    "${CMAKE_SOURCE_DIR}/deps/glad/include"
    "${CMAKE_SOURCE_DIR}/deps/glfw-3.3.2.bin.WIN64/include"
    )

set(sources
    main.cpp
    imgui/imconfig.h
    imgui/imgui.cpp
    imgui/imgui.h
    imgui/imgui_demo.cpp
    imgui/imgui_draw.cpp
    imgui/imgui_internal.h
    imgui/imgui_widgets.cpp
    imgui/imgui_tables.cpp
    imgui/imstb_rectpack.h
    imgui/imstb_textedit.h
    imgui/imstb_truetype.h
    imgui/imgui_impl_opengl3.cpp
    imgui/imgui_impl_opengl3.h
    imgui/imgui_impl_glfw.cpp
    imgui/imgui_impl_glfw.h
)

#set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} /SUBSYSTEM:WINDOWS /ENTRY:mainCRTStartup")

include(CTest)
enable_testing()

add_executable(${CMAKE_PROJECT_NAME} WIN32 ${sources})

target_link_libraries(${CMAKE_PROJECT_NAME}
    "glad"
    ${GLFW}
    ${OPENGL_gl_LIBRARY}
)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
