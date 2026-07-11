cmake_minimum_required(VERSION 3.14.4)
project(map_organizer_msgs)

find_package(neonavigation_cmake REQUIRED)

neonavigation_find_build_dependencies()
neonavigation_generate_interfaces(
    msg/OccupancyGridArray.msg
)

neonavigation_package()
