cmake_minimum_required(VERSION 3.15 FATAL_ERROR)
 
# 设置VCPKG_ROOT所在的位置
set(CMAKE_TOOLCHAIN_FILE "D://code//vcpkg//scripts//buildsystems//vcpkg.cmake")

# windows, static build, no-dll
set(VCPKG_TARGET_TRIPLET "x64-windows-static")
set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

project(grpc_test)

set(CMAKE_CXX_STANDARD 11)

find_package(gRPC CONFIG REQUIRED)
add_library(gRPC STATIC IMPORTED)

add_executable(server
  ./helloworld.grpc.pb.h
  ./helloworld.grpc.pb.cc
  ./helloworld.pb.cc
  ./helloworld.pb.h
  ./server.cc)
  
add_executable(client
  ./helloworld.grpc.pb.h
  ./helloworld.grpc.pb.cc
  ./helloworld.pb.cc
  ./helloworld.pb.h
  ./client.cc)

target_link_libraries(server PRIVATE gRPC::gpr gRPC::grpc gRPC::grpc++ gRPC::grpc++_alts gRPC::grpc++_reflection protobuf::libprotoc protobuf::libprotobuf protobuf::libprotobuf-lite)
target_link_libraries(client PRIVATE gRPC::gpr gRPC::grpc gRPC::grpc++ gRPC::grpc++_alts gRPC::grpc++_reflection protobuf::libprotoc protobuf::libprotobuf protobuf::libprotobuf-lite)
