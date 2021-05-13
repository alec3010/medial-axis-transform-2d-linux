cmake_minimum_required(VERSION 3.10)

# set the project name
project(MedialAxis2D C  CXX)

find_package (Eigen3 3.3 REQUIRED)
find_package (OpenGL REQUIRED)
find_package (GLUT REQUIRED)

#set(EIGEN_SRC Eigen)
#set(EIGEN_HEADERS Eigen/src)
set(INCLUDE_DIR include)

#add_library(Eigen ${EIGEN_SRC} ${EIGEN_HEADERS})
#target_include_directories(Eigen PRIVATE ${EIGEN_HEADERS})

# add the executable
add_library(BoundaryGenerator src/BoundaryGenerator.cpp src/BoundaryGenerator.h include/BoundaryElement.h include/Edge.h include/Utils.h)
target_include_directories(BoundaryGenerator PRIVATE ${INCLUDE_DIR})
target_link_libraries(BoundaryGenerator Eigen3::Eigen)

add_library(MedialAxisTransform src/MedialAxisTransform.cpp src/MedialAxisTransform.h include/Path.h include/Utils.h)
target_include_directories(MedialAxisTransform PRIVATE ${INCLUDE_DIR})
target_link_libraries(MedialAxisTransform Eigen3::Eigen)

#add_library(Edge Edge.h ${EIGEN_CORE})
#add_library(Utils include/Utils.h include/Parabola.h)
add_executable(MedialAxis2D src/main.cpp )
target_include_directories(MedialAxis2D PRIVATE ${INCLUDE_DIR} ${GLUT_INCLUDE_DIRS} ${OPENGL_INCLUDE_DIRS} )
target_link_libraries(MedialAxis2D BoundaryGenerator MedialAxisTransform Eigen3::Eigen ${OPENGL_LIBRARIES} ${GLUT_LIBRARY})

