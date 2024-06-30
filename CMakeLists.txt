# 指定最低的CMake版本
cmake_minimum_required(VERSION 3.10)
# 定义项目名称和支持的语言（包括CUDA）
project(MainDemo LANGUAGES C CXX CUDA)

# nvcc指定g/g++编译器路径
set(CMAKE_CUDA_FLAGS "${CMAKE_CUDA_FLAGS} -ccbin=/usr/bin/gcc-9")
set(CMAKE_CUDA_FLAGS "${CMAKE_CUDA_FLAGS} -ccbin=/usr/bin/g++-9")
# 设置编译模式
set(CMAKE_BUILD_TYPE Debug)
# 开启编译警告
set(CMAKE_CUDA_FLAGS "${CMAKE_CUDA_FLAGS} -Xcompiler -Wall")
# 设置CUDA架构
set(CMAKE_CUDA_ARCHITECTURES "61") 

# 设置源文件
# set(SOURCE_FILES ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cu ${CMAKE_CURRENT_SOURCE_DIR}/src/sha256.cuh)
set(SOURCE_FILES ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cu)
#设置输出目录
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin)
# 添加可执行文件
add_executable(main ${SOURCE_FILES})
# 设置库文件
# target_link_libraries(main ${CMAKE_CURRENT_SOURCE_DIR}/library/GL/libGL.so)
# 设置头文件
target_include_directories(main PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/src/sha256.cuh)

