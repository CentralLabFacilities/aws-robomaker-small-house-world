cmake_minimum_required(VERSION 2.8.3)
project(aws_robomaker_small_house_world)

find_package(catkin REQUIRED COMPONENTS
  gazebo_ros
)

catkin_package()

install(DIRECTORY launch models worlds maps photos routes
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

catkin_add_env_hooks(${PROJECT_NAME} 
  SHELLS sh 
  DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/env-hooks)

# Copy the rviz model for easier access in AWS RoboMaker RViz 
install(FILES ${turtlebot3_navigation_DIR}/../rviz/turtlebot3_navigation.rviz
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/rviz
  RENAME turtlebot3_navigation.rviz
)
