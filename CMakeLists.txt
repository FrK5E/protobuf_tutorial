cmake_minimum_required(VERSION 3.20 FATAL_ERROR)

project(protobuf_tutorial LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)  
 
include( files.cmake )

find_package( Protobuf REQUIRED)

include_directories(${Protobuf_INCLUDE_DIRS})
include_directories(${CMAKE_CURRENT_BINARY_DIR})
protobuf_generate_cpp( TARGET generate_files  PROTO_SRCS PROTO_HDRS addressbook.proto OUT_VAR proto_include_path )

add_library(ProtoTest addressbook.proto)
protobuf_generate(TARGET ProtoTest)
protobuf_generate(
    TARGET ProtoTest
    )
  

add_executable( program1 ${src_files} ${PROTO_SRCS} ${PROTO_HDRS} )
target_include_directories( program1 PRIVATE ${proto_include_path}  )
target_link_libraries( program1 ${Protobuf_LIBRARIES} ProtoTest )
 