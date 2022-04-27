# This file is part of "stelmap"
# Under the MIT License
# Copyright (c) 2022 Antonin Hérault

cmake_minimum_required(VERSION 3.2 FATAL_ERROR)
project(stelmap)

add_definitions(
	-DTW_STATIC
	-DTW_NO_LIB_PRAGMA
	-DTW_NO_DIRECT3D
	-DGLEW_STATIC
	-D_CRT_SECURE_NO_WARNINGS
)

# Source files
file(GLOB_RECURSE SOURCE_FILES 
	src/*.cpp)
	
# Include/header files
include_directories(
	inc/
	libs/glew/include/	# `#include <glew/?.hpp>`
	libs/glfw/include/	# `#include <glfw/?.hpp>`
	libs/glm/)			# `#include <glm/?.hpp>`
	
# Dependencies and libraries
add_subdirectory(libs)
find_package(OpenGL REQUIRED)

set(LIBS
	${OPENGL_LIBRARY}
	GLEW__
	glfw)

# Executable
add_executable(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES})
target_link_libraries(${PROJECT_NAME} ${LIBS})
