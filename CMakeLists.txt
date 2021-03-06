cmake_minimum_required(VERSION 3.20)
project(Axiome)

set(CMAKE_CXX_STANDARD 17)

find_package( OpenGL REQUIRED )

## global configs
# glfw configs
set(GLFW_BUILD_DOCS OFF CACHE BOOL "GLFW lib only" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "GLFW lib only" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "GLFW lib only" FORCE)
set(ENTT_USE_SANITIZER ON CACHE "" BOOL FORCE)


# include directories
include_directories(vendor/glfw/include)
include_directories(vendor/glm)
include_directories(vendor/spdlog/include)
include_directories(vendor/entt/src)
include_directories( ${OPENGL_INCLUDE_DIRS} )

# include dependencies
add_subdirectory(vendor/glfw)
add_subdirectory(vendor/glm)
add_subdirectory(vendor/spdlog)
add_subdirectory(vendor/entt)

# executable
add_executable(Axiome main.cpp)

# link dependency libraries
target_link_libraries(Axiome ${OPENGL_LIBRARIES} glfw spdlog)
