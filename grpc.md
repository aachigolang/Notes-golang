### Imp Links
https://github.com/jfeng45/servicetmpl


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


go get google.golang.org/grpc

$ protoc -I api/proto --go_out=plugins=grpc:pkg/api api/proto/adder.proto