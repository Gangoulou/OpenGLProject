cmake_minimum_required(VERSION 3.12)
project(OpenGL)

set(CMAKE_CXX_STANDARD 14)

set(GLEW_H /Users/gangoulou/CLionProjects/untitled2/cmake-build-debug/glew/2.2.0_1/include/GL)
set(GLFW_H /Users/gangoulou/CLionProjects/untitled2/cmake-build-debug/glfw/3.3.3/include/GLFW)
set(GLAD_H /Users/gangoulou/CLionProjects/untitled2/cmake-build-debug/glad/include/glad)
set(KH_H /Users/gangoulou/CLionProjects/untitled2/cmake-build-debug/glad/include/KHR)
include_directories(${GLEW_H} ${GLFW_H} ${GLAD_H} ${KH_H})

# Add target link
set(GLEW_LINK /Users/gangoulou/CLionProjects/untitled2/cmake-build-debug/glew/2.2.0_1/lib/libGLEW.2.2.0.dylib)
set(GLFW_LINK /Users/gangoulou/CLionProjects/untitled2/cmake-build-debug/glfw/3.3.3/lib/libglfw.3.3.dylib)
link_libraries(${OPENGL} ${GLEW_LINK} ${GLFW_LINK})

# Execute compile command
# This glad.c said in step 2 that it should be pulled into the project. Pay attention to the path
set(SOURCE_FILES "src/glad.c" "main.cpp")
add_executable(OpenGL ${SOURCE_FILES})

# mac, it's important to take this step
if (APPLE)
    target_link_libraries(OpenGL "-framework OpenGL")
    target_link_libraries(OpenGL "-framework GLUT")
endif()