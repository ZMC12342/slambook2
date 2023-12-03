cmake_minimum_required(VERSION 3.0) #新加的
option(USE_UBUNTU_20 "Set to ON if you are using Ubuntu 20.04" OFF)

find_package(Pangolin REQUIRED)
find_package(Sophus REQUIRED) #新加的

if(USE_UBUNTU_20)
    message("You are using Ubuntu 20.04, fmt::fmt will be linked")
    find_package(fmt REQUIRED)
    set(FMT_LIBRARIES fmt::fmt)
endif()

include_directories(${Sophus_INCLUDE_DIRS}) #新加的
include_directories(${Pangolin_INCLUDE_DIRS}) 
add_executable(trajectoryError trajectoryError.cpp)
target_link_libraries(trajectoryError ${Pangolin_LIBRARIES} ${FMT_LIBRARIES})
target_link_libraries(trajectoryError Sophus::Sophus) #新加的
