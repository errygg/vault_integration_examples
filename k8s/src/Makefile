.PHONY: all build

all: build

build:
	docker build --no-cache -t hashicorp/app-build:build -f ./build/docker/Dockerfile.build .
	docker create --name extract hashicorp/app-build:build
	docker cp extract:/go/src/github.com/hashicorp/app/app ./bin/app
	docker rm -f extract
	docker build --no-cache -t app -f ./build/docker/Dockerfile .
	docker tag app hashicorp/app:0.0.1
