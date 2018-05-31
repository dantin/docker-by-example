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


start: build
	@echo "Run Docker Container"
	@docker run -d -p 4567 --rm --name sinatra_app \
		-v $(shell pwd)/webapp:/opt/webapp dding/sinatra


stop:
	@echo "Stop Docker Container"
	@docker stop sinatra_app


clean:
	@echo "Clean Docker Image for this repository"
	@docker rmi dding/sinatra

