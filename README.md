### test-grpc-gateway
* Follow the installation instructions [here](https://github.com/grpc-ecosystem/grpc-gateway)
* Run the following to generate the gRPC stub
```
protoc -I/usr/local/include -I. \
  -I$GOPATH/src \
  -I$GOPATH/src/github.com/grpc-ecosystem/grpc-gateway/third_party/googleapis \
  --go_out=plugins=grpc:. \
  ./protos/helloworld.proto
  ```
* Then, run the following to generate the reverse-proxy
```
protoc -I/usr/local/include -I. \
  -I$GOPATH/src \
  -I$GOPATH/src/github.com/grpc-ecosystem/grpc-gateway/third_party/googleapis \
  --grpc-gateway_out=logtostderr=true:. \
  ./protos/helloworld.proto
```
* Make sure your service is running at localhost:9090
* Run main.go, the reverse-proxy is running at localhost:8080