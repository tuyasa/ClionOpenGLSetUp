cmake_minimum_required(VERSION 3.7)
project(OpenGLSetup)

set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES main.cpp GLAD/src/glad.c)
set(HEADER_FILES shader.h)

set(dir ${CMAKE_CURRENT_SOURCE_DIR})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${dir}/build)

include_directories(include)

#Include library files
include_directories(GLAD/include)
include_directories(glm/include)

file(COPY resources DESTINATION ${dir}/build)
file(COPY shaders DESTINATION ${dir}/build)


#Add deps
add_subdirectory(dependencies)

add_executable(OpenGLSetup ${SOURCE_FILES} ${HEADER_FILES})
target_link_libraries(OpenGLSetup glfw)
