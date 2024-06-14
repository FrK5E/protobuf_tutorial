cmake_minimum_required(VERSION 3.20 FATAL_ERROR)

# project name and enable C++ support
project(protobuf_tutorial LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)  
 
include( files.cmake )

find_package(Boost COMPONENTS system filesystem thread unit_test_framework REQUIRED)
        

add_executable( test ${src_files}  )

target_link_libraries(test PRIVATE
                      Boost::filesystem
					  Boost::unit_test_framework
					  Boost::system Boost::thread
                      )
                      
target_include_directories(test PRIVATE src )  
 