cmake_minimum_required(VERSION 2.8.3)
project(handfree_hw)

find_package(catkin REQUIRED COMPONENTS
  controller_manager
  geometry_msgs
  hardware_interface
  realtime_tools
  roscpp
  std_msgs
)

catkin_package(
  INCLUDE_DIRS include
#  LIBRARIES handfree_hw
#  CATKIN_DEPENDS controller_manager geometry_msgs hardware_interface realtime_tools roscpp std_msgs
#  DEPENDS system_lib
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  include/sdk/LIB_HF_Link/
  include/sdk/LIB_Robot_Abstract/
)

 add_executable(handfree_hw_node src/main.cpp src/transport_serial.cpp include/sdk/LIB_HF_Link/hf_link.cpp src/hf_hw.cpp src/hf_hw_ros.cpp)

 add_dependencies(handfree_hw_node handsfree_msgs_genmsg)

 target_link_libraries(handfree_hw_node
   ${catkin_LIBRARIES}
 )


