

```
cd /Users/zhaoziqi/go/src/go.opentelemetry.io/opentelemetry-demo-webstore

cp -rp pb src/productcatalogservice/proto

cd src/productcatalogservice

go mod download -x

go install google.golang.org/protobuf/cmd/protoc-gen-go
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc

protoc -I ./proto/ ./proto/demo.proto --go_out=./ --go-grpc_out=./

rm -f productcatalogservice
GOOS=linux GOARCH=amd64 go build -o productcatalogservice ./

docker build -t ghcr.io/open-telemetry/demo:0.1.0-productcatalogservice -f Dockerfile-fatsheep .
```