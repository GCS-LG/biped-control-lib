cmake_minimum_required(VERSION 2.8)

project(testErrorPreviewControl)

set(DCMAKE_BUILD_TYPE Debug)
set(EIGEN3_INCLUDE_DIR $ENV{EIGEN3_INCLUDE_DIR} CACHE PATH "Eigen installation dir(Default: $EIGEN_HOME)")
find_package(Boost COMPONENTS system thread filesystem timer)
add_definitions(-lstdc++ -std=c++11)
add_definitions(-DEIGEN_DONT_ALIGN)

include_directories(
	${Boost_INCLUDE_DIR}
	${BOOST_INCLUDE_DIRS}
	${EIGEN3_INCLUDE_DIR}
)

add_executable(testErrorPreviewControl testZMPError_PreviewController.cpp ZMPErrorPreviewController.cpp ZMPErrorPreviewController.h)

target_link_libraries(testErrorPreviewControl ${Boost_LIBRARIES})

