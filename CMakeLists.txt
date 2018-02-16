cmake_minimum_required(VERSION 3.5)

project(Caffe_BEGAN)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/bin)

#Add Caffe
find_package(OpenCV)
#find_package(Caffe)
find_package(Boost 1.54 REQUIRED COMPONENTS filesystem thread system iostreams)
find_package(OpenCV REQUIRED)

#Add source files
file(GLOB src_files "src/*.cpp")
file(GLOB header_files "include/*.h")

set(CMAKE_CXX_FLAGS "-g -Wall -Wextra -fopenmp -fPIC -std=c++11 -O2")

include_directories("include" ${CAFFE_INC_DIR} "/usr/local/cuda/include" "/usr/include")

add_executable(Caffe_BEGAN ${src_files} ${header_files})
target_link_libraries(Caffe_BEGAN ${CAFFE_LIB} gflags ${Boost_LIBRARIES} ${OpenCV_LIBS})

#target_link_libraries(Caffe_BEGAN ${Caffe_LIBRARIES})
