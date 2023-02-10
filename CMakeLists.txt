# Set minimum required CMAKE version
cmake_minimum_required(VERSION 3.8 FATAL_ERROR)
# Make sure we put all of the CMake generated projects in a sperate folder
set_property(GLOBAL PROPERTY USE_FOLDERS ON)

# Force C++17
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
# Set CUDA
enable_language(CUDA)

#create the main project
project(FFT-Project)

# Add all sources
add_subdirectory(src)

# OpenGL (glm)
set(glm_DIR "${CMAKE_CURRENT_SOURCE_DIR}/extern/glm/cmake/glm/")
find_package(glm REQUIRED)

#Add the main executable
add_executable("${PROJECT_NAME}" "${BASE_SOURCES}")

# #Add glm libraries to the main executable
target_link_libraries("${PROJECT_NAME}" glm::glm)