build:
	protoc -I. --go_out=plugins=micro:$(GOPATH)/src/github.com/tnlong1997/microservce-learner/microservice-learner/example-1/vessel-service \
    proto/vessel/vessel.proto
	protoc -I. --go_out=plugins=micro:. \
	  proto/vessel/vessel.proto

	GOOS=linux GOARCH=amd64 go build
	docker build -t vessel-service .

run:
	docker run -p 50052:50051 \
		-e MICRO_SERVER_ADDRESS=:50051 \
		-e MICRO_REGISTRY=mdns cart-service
