cmake_minimum_required(VERSION 3.14.4)
project(safety_limiter_msgs)

find_package(neonavigation_cmake REQUIRED)

neonavigation_find_build_dependencies()
neonavigation_generate_interfaces(
    msg/SafetyLimiterStatus.msg
)

neonavigation_package()