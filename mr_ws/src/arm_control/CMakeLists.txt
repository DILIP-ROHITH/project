cmake_minimum_required(VERSION 3.1.3)
project(arm_control)

find_package(catkin REQUIRED
  class_loader
  costmap_2d
  cv_bridge
  dynamic_reconfigure
  eigen_conversions
  geometry_msgs
  droid
  image_geometry
  image_transport
  laser_geometry
  message_filters
  message_generation
  move_base
  move_base_msgs
  nav_msgs
  nodelet
  pcl_conversions
  pcl_ros
  pluginlib
  roscpp
  rosgraph_msgs
  rospy
  rviz
  sensor_msgs
  std_msgs
  std_srvs
  stereo_msgs
  tf
  tf2_ros
  tf_conversions
  visualization_msgs
  map_server
)

catkin_package()

install(DIRECTORY launch DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  PATTERN "setup_assistant.launch" EXCLUDE)
install(DIRECTORY config DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
