cmake_minimum_required(VERSION 3.10)
project(ffmpeg-examples)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake")

find_package(FFMPEG REQUIRED
  COMPONENTS
  avutil
  avcodec
  avformat
  avfilter
  swscale
  swresample
)
include_directories(${FFMPEG_INCLUDE_DIRS})

add_executable(demuxing_decoding examples/demuxing_decoding.c)
target_link_libraries(demuxing_decoding PRIVATE ${FFMPEG_LIBRARIES})