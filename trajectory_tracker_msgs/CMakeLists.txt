cmake_minimum_required(VERSION 3.14.4)
project(trajectory_tracker_msgs)

find_package(neonavigation_cmake REQUIRED)

neonavigation_find_build_dependencies()
neonavigation_generate_interfaces(
  msg/PathWithVelocity.msg
  msg/PoseStampedWithVelocity.msg
  msg/TrajectoryServerStatus.msg
  msg/TrajectoryTrackerStatus.msg
)

neonavigation_add_library(converter INTERFACE
)
neonavigation_target_link_libraries(converter
  INTERFACE
    geometry_msgs
    nav_msgs
)

if (BUILD_TESTING)
  set(THREADS_PREFER_PTHREAD_FLAG ON)
  find_package(Threads REQUIRED)

  find_package(ament_cmake_gtest REQUIRED)
  ament_add_gtest(test_path_with_velocity_conversion test/src/test_path_with_velocity_conversion.cpp)

  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()

  target_include_directories(test_path_with_velocity_conversion PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
  )

  rosidl_get_typesupport_target(cpp_typesupport_target
    ${PROJECT_NAME} rosidl_typesupport_cpp
  )

  target_link_libraries(test_path_with_velocity_conversion
    rclcpp::rclcpp ${geometry_msgs_TARGETS} ${std_msgs_TARGETS} ${nav_msgs_TARGETS} ${cpp_typesupport_target}
  )

endif()

neonavigation_package(EXPORT_TARGETS)
