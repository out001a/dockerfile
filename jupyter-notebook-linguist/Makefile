PWD := $(shell pwd)

IMAGE_NAME := $(shell cat ./IMAGE_NAME)
CONTAINER_NAME := $(shell echo $(IMAGE_NAME) | awk -F':' '{print $$1}')
CONTAINER_HOME := /home/jupyter

.PHONY: build push run rm stop exec logs rmi

build:
	docker build -t $(IMAGE_NAME) .

push:
	docker push $(IMAGE_NAME)

run: rm
	docker run -d -it --name $(CONTAINER_NAME) -p 8899:8899 \
		-v $(PWD)/notes:$(CONTAINER_HOME)/notes \
		$(IMAGE_NAME)

rm: stop
	docker rm $(CONTAINER_NAME); exit 0

stop:
	docker stop $(CONTAINER_NAME); exit 0

exec:
	docker exec -it $(CONTAINER_NAME) /bin/bash

logs:
	docker logs $(CONTAINER_NAME)

rmi:
	docker images | fgrep '<none>' | awk '{print $$3}' | xargs docker rmi
