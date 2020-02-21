REPOSITORY ?= sigwindowstools/wins-admission-controller

IMG := $(REPOSITORY):latest

build:
	go build -mod vendor -o bin/wins-controller

docker-build:
	docker build --pull . -t ${IMG}

docker-push: docker-build
	docker push ${IMG}

