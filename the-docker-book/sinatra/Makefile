#
# Makefile for Sinatra Application
#
# version 1.0 2018-05-31
#

.PHONY: build clean start stop


default: build


build:
	@echo "Build Docker Image for Sinatra Application"
	@docker build -t dding/sinatra .
	@echo "Build Redis Image for Sinatra Application"
	@cd redis; docker build -t dding/redis .


start: build
	@echo "Create Network"
	@docker network create sinatra_network
	@echo "Create Redis Container"
	@docker run -d -p 6379 --rm --net=sinatra_network --name db dding/redis
	@echo "Create Sinatra Container"
	@docker run -d -p 4567 --rm --name sinatra_app \
		--net=sinatra_network \
		-v $(shell pwd)/webapp:/opt/webapp dding/sinatra


stop:
	@echo "Stop Sinatra Container"
	@docker stop sinatra_app
	@echo "Stop Redis Container"
	@docker stop db
	@echo "Remove Network"
	@docker network rm sinatra_network


clean:
	@echo "Clean Docker Image for this repository"
	@docker rmi dding/sinatra

