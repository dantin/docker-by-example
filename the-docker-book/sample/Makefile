#
# Makefile for static_website
# version 1.0 2018-05-31
#

.PHONY: build clean start stop


default: build


build:
	@echo "Build Docker Image for static website"
	@docker build -t dding/nginx .


start: build
	@echo "Run Docker Container using files in 'website' directory"
	@docker run -d -p 80 --rm --name static_website \
		-v $(shell pwd)/website:/var/www/html/website \
		dding/nginx nginx


stop:
	@echo "Stop Docker Container"
	@docker stop static_website


clean:
	@echo "Clean Docker Image for this repository"
	@docker rmi dding/nginx

