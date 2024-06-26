cmake_minimum_required(VERSION 2.8.12)
project(CppMeshRenderer)

include_directories(glad)
add_definitions(-DUSE_GLAD)

add_executable(query_devices glad/egl.cpp glad/gl.cpp query_devices.cpp)
add_executable(test_device glad/egl.cpp glad/gl.cpp test_device.cpp)


IF(WIN32)
  SET(PLATFORM_LIBS)
  IF(NOT CMAKE_CL_64)
    # tell the compiler to use stdcall calling convention even in x86 where cdecl is default
    # this is a simple workaround for Win32 x86 support 
    SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /Gz")
  ENDIF()
ELSE(WIN32)
  SET(PLATFORM_LIBS dl pthread)
ENDIF(WIN32)

target_link_libraries(query_devices ${PLATFORM_LIBS})
target_link_libraries(test_device ${PLATFORM_LIBS})