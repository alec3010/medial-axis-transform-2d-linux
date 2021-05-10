cmake_minimum_required(VERSION 3.10)

# set the project name
project(MedialAxis2D)

# add the executable
add_library(BoundaryGenerator src/BoundaryGenerator.cpp include/BoundaryGenerator.h include/Utils.h)
add_library(BoundaryElement src/BoundaryElement.cpp include/BoundaryElement.h include/Edge.h)
add_library(MedialAxisTransform src/MedialAxisTransform.cpp include/MedialAxisTransform.h include/Path.h include/Utils.h)
add_executable(MedialAxis2D src/main.cpp )

