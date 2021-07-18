cmake_minimum_required(VERSION 3.11)
PROJECT(main)

#step1. build lib
set(INC_DIR ${PROJECT_SOURCE_DIR}/inc)
add_library(hellolib STATIC ${INC_DIR}/hello.cpp ${INC_DIR}/hello.h) # 生成一个库文件
SET(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)

#step2.build target exe
include_directories(${PROJECT_SOURCE_DIR})
ADD_EXECUTABLE(demoexe ${PROJECT_SOURCE_DIR}/src/main.cpp ${INC_DIR}/hello.h) 
TARGET_LINK_LIBRARIES(demoexe hellolib) #一定要link到.a文件
message(STATUS "Current Cmake dir is: ${INC_DIR}")



