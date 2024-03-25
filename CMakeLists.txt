cmake_minimum_required(VERSION 3.13)
project(opengl)

set(CMAKE_CXX_STANDARD 11)

#设置一些OpenGL头文件所在目录的宏
set(GLEW_H /usr/local/Cellar/glew/2.2.0_1/include/GL)
set(GLFW_H /usr/local/Cellar/glfw/3.3.9/include/GLFW)
set(GLAD_H /usr/local/include/)
set(GLAD_H /usr/local/include/glad)
set(KH_H /usr/local/include/KHR)
set(ASSIMP_H  /usr/local/Cellar/assimp/5.3.1/include)
#包含上述头文件所在目录
include_directories(${GLEW_H} ${GLFW_H} ${GLAD_H} ${KH_H} ${ASSIMP_H})
include_directories(${PROJECT_SOURCE_DIR}/thirdparty/glm)

#设置OpenGL库所在位置，并链接
set(GLEW_LINK /usr/local/Cellar/glew/2.2.0_1/lib/libGLEW.2.2.0.dylib)
set(GLFW_LINK /usr/local/Cellar/glfw/3.3.9/lib/libglfw.3.3.dylib)
set(ASSIMP_LINK /usr/local/Cellar/assimp/5.3.1/lib/libassimp.5.3.0.dylib)
link_libraries(${OPENGL} ${GLEW_LINK} ${GLFW_LINK} ${ASSIMP_LINK})



add_executable(opengl
        main.cpp
        src/glad.c src/shader_s.h src/stb_image.h src/stb_image.cpp camera_class.cpp camera.h basic_lighting_specular.cpp mesh.h model_loading.cpp model.h)

if (APPLE)
    target_link_libraries(opengl "-framework OpenGL")
    target_link_libraries(opengl "-framework GLUT")
endif()