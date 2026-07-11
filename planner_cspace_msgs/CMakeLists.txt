cmake_minimum_required(VERSION 3.14.4)
project(planner_cspace_msgs)

find_package(neonavigation_cmake REQUIRED)

neonavigation_find_build_dependencies()
neonavigation_generate_interfaces(
    msg/PlannerStatus.msg
    action/MoveWithTolerance.action
)
neonavigation_package()
