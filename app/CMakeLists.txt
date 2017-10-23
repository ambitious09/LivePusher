cmake_minimum_required(VERSION 3.4.1)

add_subdirectory(src/main/cpp/include/librtmp)
#添加动态库
file(GLOB my_source src/main/cpp/*.cpp src/main/cpp/*.c)
add_library(pusher SHARED ${my_source})

#设置变量 指向ffmpeg静态库目录
set(my_lib_path ${CMAKE_SOURCE_DIR}/src/main/cpp/lib/${ANDROID_ABI})
#添加静态库 并设置库路径
add_library(faac STATIC IMPORTED)
set_target_properties(faac PROPERTIES IMPORTED_LOCATION ${my_lib_path}/libfaac.a)
add_library(x264 STATIC IMPORTED)
set_target_properties(x264 PROPERTIES IMPORTED_LOCATION ${my_lib_path}/libx264.a)
#设置头文件查找目录
include_directories(src/main/cpp/include)

#编译链接
target_link_libraries(pusher log rtmp faac x264  )