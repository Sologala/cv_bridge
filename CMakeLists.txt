cmake_minimum_required(VERSION 3.0.2)
project(cv_bridge)

find_package(catkin REQUIRED COMPONENTS rosconsole sensor_msgs)

find_package(OpenCV QUIET)

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES ${PROJECT_NAME}
  CATKIN_DEPENDS rosconsole sensor_msgs
  DEPENDS OpenCV
  CFG_EXTRAS cv_bridge-extras.cmake
)


set(CV_BRIDGE_SRC
  src/cv_bridge.cpp 
  src/rgb_colors.cpp
)

include_directories(
  # ./include/
  ${catkin_INCLUDE_DIRS}
  ${Boost_INCLUDE_DIRS}
  ${OpenCV_INCLUDE_DIRS}
)

add_library(${PROJECT_NAME} ${CV_BRIDGE_SRC})

target_include_directories( ${PROJECT_NAME} PUBLIC
./include/
)


target_link_libraries(${PROJECT_NAME} PRIVATE
  ${OpenCV_LIBRARIES}
  ${catkin_LIBRARIES}
  ${Boost_LIBRARY_DIRS}
)

add_dependencies(${PROJECT_NAME} ${catkin_EXPORTED_TARGETS})


install(TARGETS ${PROJECT_NAME}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_GLOBAL_BIN_DESTINATION}
)


install(
  DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
)
