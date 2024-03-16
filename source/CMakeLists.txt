# SSAS - Simple Smart Automotive Software
# Copyright (C) 2024 Parai Wang <parai@foxmail.com>

set(VDDS_INCLUDE ${PROJECT_SOURCE_DIR}/include)

set(VDDS_SOURCE
    Log.cpp
    named_semaphore.cpp
    shared_memory.cpp
    vring.cpp
)

set(VDDS_LIBS)

if ( CMAKE_SYSTEM_NAME MATCHES "MSYS" )
list(APPEND VDDS_INCLUDE platform/win/include)
list(APPEND VDDS_SOURCE platform/win/mman.cpp platform/win/semaphore.cpp)
elseif ( CMAKE_SYSTEM_NAME MATCHES "Linux" )
list(APPEND VDDS_LIBS pthread rt)
else()
message(ERROR "CMAKE_SYSTEM_NAME is ${CMAKE_SYSTEM_NAME} which is not supported" )
endif()

add_library(VDDS STATIC ${VDDS_SOURCE})
target_compile_definitions(VDDS PUBLIC USE_STD_PRINTF)
target_include_directories(VDDS PUBLIC ${VDDS_INCLUDE})
target_link_libraries(VDDS PUBLIC ${VDDS_LIBS})

