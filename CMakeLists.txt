cmake_minimum_required(VERSION 3.16)
project(PaperPlane)

set(CMAKE_CXX_STANDARD 14)

# add includes
set(GLEW_H /usr/local/Cellar/glew/2.2.0_1/include/GL)
set(GLFW_H /usr/local/Cellar/glfw/3.3.6/include/GLFW)
include_directories(
        ${GLEW_H}
        ${GLFW_H}
        include)

# add target libraries
set(GLEW_LINK /usr/local/Cellar/glew/2.2.0_1/lib/libGLEW.2.2.dylib)
set(GLFW_LINK /usr/local/Cellar/glfw/3.3.6/lib/libglfw.3.dylib)
link_libraries(${OPENGL} ${GLEW_LINK} ${GLFW_LINK})

# execute compile
set(SOURCE_FILES
        src/main.cpp
        src/glad.c)
add_executable(PaperPlan ${SOURCE_FILES})

if (APPLE)
    target_link_libraries(PaperPlan "-framework OpenGL")
    target_link_libraries(PaperPlan "-framework GLUT")
endif()