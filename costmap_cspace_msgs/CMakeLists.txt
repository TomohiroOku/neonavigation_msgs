cmake_minimum_required(VERSION 3.14.4)
project(costmap_cspace_msgs)

find_package(neonavigation_cmake REQUIRED)

neonavigation_find_build_dependencies()
neonavigation_generate_interfaces(
    msg/CSpace3D.msg
    msg/CSpace3DUpdate.msg
    msg/MapMetaData3D.msg
)

neonavigation_package()