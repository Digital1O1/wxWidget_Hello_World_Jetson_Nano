cmake_minimum_required(VERSION 3.16)
project(wxWidget_Hello_World)

# Set the main wxWidgets include directory
set(wxWidget_INCLUDE_DIR "/home/ctnano/wxWidgets/include")

# Set the additional include path for wxWidgets (if needed)
set(wxWidget_ADDITIONAL_INCLUDE_DIR "/home/ctnano/wxWidgets/buildgtk/lib/wx/include/gtk3-unicode-3.3")

set(SOURCES
    main.cpp
)

# Locate/configure external libraries/packages your project may need
find_package(wxWidgets REQUIRED net core base)

message(STATUS "                                                                         ")
message(STATUS "-------------------------------------------------------------------------")
message(STATUS "    ******** wxWidgets library status ********                           ")
message(STATUS "    wxWidget_INCLUDE_DIR                 : ${wxWidget_INCLUDE_DIR}")
message(STATUS "    wxWidget_ADDITIONAL_INCLUDE_DIR      : ${wxWidget_ADDITIONAL_INCLUDE_DIR}")
message(STATUS "-------------------------------------------------------------------------")
message(STATUS "                                                                         ")

# Set C++ standard to C++11
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(wxWidget_Hello_World ${SOURCES})

# Specifies include directories for a specific target like an executable or library
target_include_directories(wxWidget_Hello_World PRIVATE ${wxWidget_INCLUDE_DIR})
target_include_directories(wxWidget_Hello_World PRIVATE ${wxWidget_ADDITIONAL_INCLUDE_DIR})

# Just specifies the libraries a target needs
target_link_libraries(wxWidget_Hello_World ${wxWidgets_LIBRARIES})

# Create a custom target to clean the build directory
add_custom_target(clean_build
    COMMAND ${CMAKE_COMMAND} -E remove_directory " ${CMAKE_BINARY_DIR}/* "
    COMMENT " Cleaning the build directory "
)
