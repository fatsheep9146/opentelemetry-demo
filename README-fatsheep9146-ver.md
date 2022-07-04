
# start all containers

docker compose -f compose-fatsheep9146-ver.yml up 

# build for one service

```

export SERVICE=
cd /Users/zhaoziqi/go/src/go.opentelemetry.io/opentelemetry-demo-webstore
cp -rp pb src/${SERVICE}/proto
cd src/${SERVICE}
go mod download -x
go install google.golang.org/protobuf/cmd/protoc-gen-go
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc
protoc -I ./proto/ ./proto/demo.proto --go_out=./ --go-grpc_out=./
rm -f ${SERVICE}
GOOS=linux GOARCH=amd64 go build -o ${SERVICE} ./
docker build -t ghcr.io/open-telemetry/demo:0.1.0-${SERVICE} -f Dockerfile-fatsheep .

```

Dockerfile-fatsheep9146 demo
```

FROM alpine AS release

WORKDIR /usr/src/app/

COPY ./products.json ./
COPY ./productcatalogservice/ ./

EXPOSE 3550
ENTRYPOINT [ "./productcatalogservice" 

```
