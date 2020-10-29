cmake_minimum_required(VERSION 3.5)

project (cal_pnp)

find_package(OpenCV REQUIRED)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DOPENCV")
MESSAGE( " *** OpenCV_INCLUDE_DIRS : " ${OpenCV_INCLUDE_DIRS} )
MESSAGE( " *** OpenCV_LIB_DIRS : " ${OpenCV_LIB_DIRS} )
MESSAGE( " *** OpenCV_LIBS : " ${OpenCV_LIBS} )

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src  ${OPENCV_INCLUDE_DIRS})
add_library(calpnp SHARED src/CamCal.cpp src/Cfg.cpp)
target_link_libraries(calpnp ${OpenCV_LIBS})


add_executable(cal_pnp_exec src/main.cpp)
target_link_libraries(cal_pnp_exec calpnp)