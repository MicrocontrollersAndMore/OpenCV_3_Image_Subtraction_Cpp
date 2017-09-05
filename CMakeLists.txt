# cmake needs this line
cmake_minimum_required(VERSION 2.8)

project(learn-cmake)

# Find OpenCV, you may need to set OpenCV_DIR variable
# to the absolute path to the directory containing OpenCVConfig.cmake file
# via the command line or GUI
find_package(OpenCV REQUIRED)

# If the package has been found, several variables will
# be set, you can find the full list with descriptions
# in the OpenCVConfig.cmake file.
# Print some message showing some of them
message(STATUS "OpenCV library status:")
message(STATUS "    version: ${OpenCV_VERSION}")
message(STATUS "    libraries: ${OpenCV_LIBS}")
message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")

if(CMAKE_VERSION VERSION_LESS "2.8.11")
  # Add OpenCV headers location to your include paths
  include_directories(${OpenCV_INCLUDE_DIRS})
endif()

include_directories(${PROJECT_SRC_DIR})
add_library(blob blob.cpp)

# add_executable(image_in_window image_in_window.cpp)
# target_link_libraries(image_in_window ${OpenCV_LIBS})
add_executable(main main.cpp)
target_link_libraries(main ${OpenCV_LIBS} blob)
