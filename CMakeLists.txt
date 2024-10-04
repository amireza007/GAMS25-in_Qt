cmake_minimum_required(VERSION 3.15)

project(transport4 C CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

INCLUDE_DIRECTORIES("${CMAKE_CURRENT_SOURCE_DIR}/../../C/api"
    "${CMAKE_CURRENT_SOURCE_DIR}/../api")

find_package(Qt6 REQUIRED COMPONENTS Core Gui Widgets)

set(LIBRARY_OUTPUT_PATH "${CMAKE_BINARY_DIR}")
set(EXECUTABLE_OUTPUT_PATH "${CMAKE_BINARY_DIR}")

#add_subdirectory(libs)
IF (WIN32)
  SET(VSVERSION "vs2017" CACHE STRING "Visual Studio version")
  LINK_DIRECTORIES("${CMAKE_CURRENT_SOURCE_DIR}/")
ELSE()
  LINK_DIRECTORIES("${CMAKE_CURRENT_SOURCE_DIR}/")
ENDIF()

add_executable(${PROJECT_NAME}
    "transport4.cpp")

message("______________\n")

file(GLOB LIBFI "*.dll" "*.lib" "*.exp")
foreach(DLL ${LIBFI})
    file(COPY ${DLL} DESTINATION ${EXECUTABLE_OUTPUT_PATH})
endforeach()
find_library(MYLIBS NAMES d3dcompiler_47 libEGL libGLESV2 opengl32sw Qt5Core Qt5Gui Qt5Sql Qt5Svg Qt5Widgets gamscpp PATHS ${CMAKE_CURRENT_SOURCE_DIR})

TARGET_LINK_LIBRARIES(${PROJECT_NAME}
    Qt6::Core
    Qt6::Gui
    Qt6::Widgets
    ${MYLIBS}
)
