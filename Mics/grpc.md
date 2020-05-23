grpc

### Setting up protoc in ubuntu 

sudo apt-get install autoconf automake libtool curl make g++ unzip -y
git clone https://github.com/google/protobuf.git
cd protobuf
git submodule update --init --recursive
./autogen.sh
./configure
make
make check
sudo make install
sudo ldconfig

#### Useful links
grpc building tut (advance)
https://www.youtube.com/channel/UC6MtKoJrZLNELkS96F99eIQ/videos

https://dev.to/koddr/enter-to-grpc-in-go-first-server-4a5g#ch-2

###Protoc Example

$ protoc -I api/proto --go_out=plugins=grpc:pkg/api api/proto/adder.proto

$ tree .
.
├── Makefile
├── go.mod
├── go.sum
├── api
│   └── proto
│       └── adder.proto     <-- proto file
├── cmd
│   └── server
│       └── main.go         <-- main app
└── pkg
    ├── adder
    │   └── grpcserver.go   <-- methods for gRPC server
    └── api
        └── adder.pb.go     <-- auto generated code from .proto file
