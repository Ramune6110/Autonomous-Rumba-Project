cmake_minimum_required(VERSION 3.0.2)
project(waypoints_navigation)

find_package(catkin REQUIRED COMPONENTS
  actionlib
  geometry_msgs
  move_base_msgs
  roscpp
  tf
  visualization_msgs
)

find_package(PkgConfig)
pkg_search_module(yaml-cpp REQUIRED yaml-cpp)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES waypoint_specification
  CATKIN_DEPENDS actionlib geometry_msgs move_base_msgs roscpp tf visualization_msgs
#  DEPENDS system_lib
)

include_directories(
# include
  ${catkin_INCLUDE_DIRS}
  ${yaml-cpp_INCLUDE_DIRS}
)

add_executable(save_odometry src/save_odometry.cpp)
target_link_libraries(save_odometry ${catkin_LIBRARIES})

add_executable(waypoints_publish src/waypoints_publish.cpp)
target_link_libraries(waypoints_publish ${catkin_LIBRARIES} ${yaml-cpp_LIBRARIES})