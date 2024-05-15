cmake_minimum_required(VERSION 2.8.12)
project(CppMeshRenderer)

include_directories(glad)
add_definitions(-DUSE_GLAD)

add_executable(query_devices glad/egl.cpp glad/gl.cpp query_devices.cpp)
add_executable(test_device glad/egl.cpp glad/gl.cpp test_device.cpp)


IF(WIN32)
  SET(PLATFORM_LIBS)
ELSE(WIN32)
  SET(PLATFORM_LIBS dl pthread)
ENDIF(WIN32)

target_link_libraries(query_devices ${PLATFORM_LIBS})
target_link_libraries(test_device ${PLATFORM_LIBS})