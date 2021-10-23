cmake_minimum_required(VERSION 3.0.2)
project(turtlbot3_nav)

## Compile as C++11, supported in ROS Kinetic and newer
# add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
    cmake_modules
    dynamic_reconfigure
    geometry_msgs
    map_msgs
    message_filters
    message_generation
    nav_msgs
    pluginlib
    roscpp
    rospy
    sensor_msgs
    std_msgs
    tf2
    tf2_geometry_msgs
    tf2_ros
    tf2_sensor_msgs
    visualization_msgs
    costmap_2d
    pcl_ros
)

find_package(PCL REQUIRED)
#find_package(Eigen3 REQUIRED)
#find_package(Boost REQUIRED COMPONENTS system thread)
include_directories(
    #include
    ${catkin_INCLUDE_DIRS}
    #${EIGEN3_INCLUDE_DIRS}
    #${Boost_INCLUDE_DIRS}
    ${PCL_INCLUDE_DIRS}
)
#add_definitions(${EIGEN3_DEFINITIONS})

generate_messages(
    DEPENDENCIES
        std_msgs
        geometry_msgs
        map_msgs
)

# dynamic reconfigure
#generate_dynamic_reconfigure_options(
#  cfg/DepthCameraPlugin.cfg
#)

#add_library(tracer_2dnav
 # plugins/depth_camera_obstacle_layer.cpp
 # src/observation_buffer.cpp
#)

#add_dependencies(tracer_2dnav ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
#target_link_libraries(tracer_2dnav
#  ${catkin_LIBRARIES} ${Boost_LIBRARIES}
#)

#catkin_install_python(PROGRAMS src/imu_tf.py
#  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
#)
#"catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES tracer_2dnav
#  CATKIN_DEPENDS roscpp rospy
#  DEPENDS system_lib
#)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)

## Declare a C++ library
# add_library(${PROJECT_NAME}
#   src/${PROJECT_NAME}/tracer_2dnav.cpp
# )

## Add cmake target dependencies of the library
## as an example, code may need to be generated before libraries
## either from message generation or dynamic reconfigure
# add_dependencies(${PROJECT_NAME} ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})

## Declare a C++ executable
## With catkin_make all packages are built within a single CMake context
## The recommended prefix ensures that target names across packages don't collide
# add_executable(${PROJECT_NAME}_node src/tracer_2dnav_node.cpp)

## Rename C++ executable without prefix
## The above recommended prefix causes long target names, the following renames the
## target back to the shorter version for ease of user use
## e.g. "rosrun someones_pkg node" instead of "rosrun someones_pkg someones_pkg_node"
# set_target_properties(${PROJECT_NAME}_node PROPERTIES OUTPUT_NAME node PREFIX "")

## Add cmake target dependencies of the executable
## same as for the library above
# add_dependencies(${PROJECT_NAME}_node ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})

## Specify libraries to link a library or executable target against
# target_link_libraries(${PROJECT_NAME}_node
#   ${catkin_LIBRARIES}
# )

#############
## Install ##
#############

# all install targets should use catkin DESTINATION variables
# See http://ros.org/doc/api/catkin/html/adv_user_guide/variables.html

## Mark executable scripts (Python etc.) for installation
## in contrast to setup.py, you can choose the destination
# catkin_install_python(PROGRAMS
#   scripts/my_python_script
#   DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
# )

## Mark executables for installation
## See http://docs.ros.org/melodic/api/catkin/html/howto/format1/building_executables.html
# install(TARGETS ${PROJECT_NAME}_node
#   RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
# )

## Mark libraries for installation
## See http://docs.ros.org/melodic/api/catkin/html/howto/format1/building_libraries.html
# install(TARGETS ${PROJECT_NAME}
#   ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#   LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#   RUNTIME DESTINATION ${CATKIN_GLOBAL_BIN_DESTINATION}
# )

## Mark cpp header files for installation
# install(DIRECTORY include/${PROJECT_NAME}/
#   DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
#   FILES_MATCHING PATTERN "*.h"
#   PATTERN ".svn" EXCLUDE
# )

## Mark other files for installation (e.g. launch and bag files, etc.)

#install(TARGETS
#    tracer_2dnav
#    ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#    LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#    RUNTIME DESTINATION ${CATKIN_GLOBAL_BIN_DESTINATION}
#)

#install(FILES costmap_plugins.xml
#  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
#)

#install(DIRECTORY include/tracer_2dnav/
#  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
#  PATTERN ".svn" EXCLUDE
#)


install(DIRECTORY 
 # include
 # cfg
  launch 
  param
  map
 # plugins 
 # src
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
