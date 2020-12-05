# grpc 示例 #

## vcpkg
    git clone https://github.com/Microsoft/vcpkg.git
    cd vcpkg
    bootstrap-vcpkg.bat
    
    vcpkg install grpc:x64-windows-static # 64bit windows static library
    vcpkg install grpc:x64-windows # 64bit windows dll library

## generate .cc/.h
    protoc -cpp_out=. ./hellowrod.proto
    protoc.exe --grpc_out=./ --plugin=protoc-gen-grpc=/path/to/grpc_cpp_plugin.exe ./helloworld.proto

## cmake
    mkdir build
    cd build
    cmake ../ -G "Visual Studio 15 2017 Win64"
