# SSAS - Simple Smart Automotive Software
# Copyright (C) 2024 Parai Wang <parai@foxmail.com>

add_executable(VDDSHwPub hello_world_publisher.cpp)
target_link_libraries(VDDSHwPub PRIVATE VDDS)

add_executable(VDDSHwSub hello_world_subscriber.cpp)
target_link_libraries(VDDSHwSub PRIVATE VDDS)
