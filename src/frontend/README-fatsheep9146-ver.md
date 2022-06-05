
# build frontend in two-steps way

first build binary, then build image.

build binary by 

```
GOARCH=amd64 GOOS=linux go build -o server 
```

build image 
```
export TAG=
docker build -t otel/frontend:${TAG} -f Dockerfile-fatsheep9146-ver .
```

