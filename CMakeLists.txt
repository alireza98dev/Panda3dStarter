cmake_minimum_required(VERSION 3.0.0)
project(mygame VERSION 0.1.0)

include(CTest)
enable_testing()
find_package(OpenGL REQUIRED)

add_executable(${PROJECT_NAME} src/main.cpp)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
set(PANDA3D_SDK_DIR "c:/Panda3D-1.10.12-x64")
set(PANDA3D_LIB_DIR ${PANDA3D_SDK_DIR}/lib)
set(PANDA3D_INCLUDE_DIR ${PANDA3D_SDK_DIR}/include)


target_include_directories(${PROJECT_NAME} PUBLIC SYSTEM $<BUILD_INTERFACE:${PANDA3D_INCLUDE_DIR}>)
set(PANDA3D_LIBS
    ${PANDA3D_LIB_DIR}/libp3framework.lib
    ${PANDA3D_LIB_DIR}/libpanda.lib
    ${PANDA3D_LIB_DIR}/libpandaexpress.lib
    ${PANDA3D_LIB_DIR}/libp3dtool.lib
    ${PANDA3D_LIB_DIR}/libp3dtoolconfig.lib
    ${PANDA3D_LIB_DIR}/libp3direct.lib
)

target_link_libraries(${PROJECT_NAME} PRIVATE ${PANDA3D_LIBS})

include(CPack)
