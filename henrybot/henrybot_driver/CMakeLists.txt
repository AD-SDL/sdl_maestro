cmake_minimum_required(VERSION 3.5.1)
cmake_policy(SET CMP0048 NEW)
project(henrybot_driver)

find_package(catkin REQUIRED COMPONENTS
  actionlib_msgs
  diagnostic_msgs
  dynamic_reconfigure
  geometry_msgs
  mir_actions
  mir_msgs
  mir_driver
  move_base_msgs
  nav_msgs
  rosgraph_msgs
  roslaunch
  rospy
  rospy_message_converter
  sensor_msgs
  std_msgs
  tf
  visualization_msgs
)

catkin_python_setup()

###################################
## catkin specific configuration ##
###################################
catkin_package(
  CATKIN_DEPENDS
    actionlib_msgs
    diagnostic_msgs
    dynamic_reconfigure
    geometry_msgs
    mir_actions
    mir_msgs
    mir_driver
    move_base_msgs
    nav_msgs
    rosgraph_msgs
    rospy_message_converter
    sensor_msgs
    std_msgs
    tf
    visualization_msgs
)

#############
## Install ##
#############

catkin_install_python(PROGRAMS
  nodes/mir_250_bridge.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

# Mark other files for installation (e.g. launch and bag files, etc.)
install(DIRECTORY
  launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

#############
## Testing ##
#############

roslaunch_add_file_check(launch)
