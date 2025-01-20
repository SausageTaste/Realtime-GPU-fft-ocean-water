cmake_minimum_required(VERSION 3.12)

if (NOT CMAKE_TOOLCHAIN_FILE)
    set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake")
endif()

project(Poseidon
    VERSION 0.1.0
    LANGUAGES CXX
)

find_package(GLEW REQUIRED)
find_package(glfw3 CONFIG REQUIRED)
find_package(glm CONFIG REQUIRED)
find_package(GLUT REQUIRED)
find_package(Stb REQUIRED)

set(src_dir ${CMAKE_CURRENT_SOURCE_DIR}/Poseidon/Poseidon)

add_executable(${PROJECT_NAME}
    ${src_dir}/main.cpp
    ${src_dir}/ShaderProgram.cpp
    ${src_dir}/Texture.cpp
)
target_include_directories(${PROJECT_NAME} PRIVATE
    ${src_dir}
    ${Stb_INCLUDE_DIR}
)
target_link_libraries(${PROJECT_NAME} PRIVATE
    GLEW::GLEW
    glfw
    glm::glm
    GLUT::GLUT
)
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_17)
