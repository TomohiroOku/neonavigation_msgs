cmake_minimum_required(VERSION 3.14.4)
project(neonavigation_metrics_msgs)

find_package(neonavigation_cmake REQUIRED)

neonavigation_find_build_dependencies()
neonavigation_generate_interfaces(
  msg/Metric.msg
  msg/Metrics.msg
)

neonavigation_add_library(helper INTERFACE)

if(BUILD_TESTING)

  find_package(ament_cmake_gtest REQUIRED)
  ament_add_gtest(test_helper test/src/test_helper.cpp)
  target_include_directories(test_helper PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
  )
  rosidl_get_typesupport_target(cpp_typesupport_target
    ${PROJECT_NAME} rosidl_typesupport_cpp
  )
  target_link_libraries(test_helper ${cpp_typesupport_target})

  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

neonavigation_package(EXPORT_TARGETS)