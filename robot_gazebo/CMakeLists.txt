cmake_minimum_required(VERSION 2.8.3)
project(robot_gazebo)

find_package(catkin REQUIRED COMPONENTS
  sensor_msgs
  std_msgs
  message_generation
  rospy
)

generate_messages(
  DEPENDENCIES
  std_msgs
)

catkin_package(
 CATKIN_DEPENDS sensor_msgs std_msgs message_runtime rospy
 DEPENDS system_lib
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

install(DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

install(DIRECTORY worlds
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

install(DIRECTORY scripts
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

catkin_install_python(PROGRAMS scripts/gazebo_joy.py
                      DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

