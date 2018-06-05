#
# Makefile for jekyll
#
# version 1.0 2018-06-05
#

.PHONY: build clean start stop


default: build


build:
	@echo "Build Docker Image for Jekyll image"
	@cd jekyll; docker build -t dding/jekyll .
	@echo "Build Docker Image for Apache image"
	@cd apache; docker build -t dding/apache .


generate: build
	@echo "Generate static website in '/tmp/james_blog_html' directory"
	@docker run --name james_blog --rm \
		-v $(shell pwd)/james_blog:/data/ \
		-v /tmp/james_blog_html:/var/www/html/ \
		dding/jekyll

start: generate
	@echo "Start Apache Continer"
	@docker run -d --rm --name jekyll_static_website -P \
		-v /tmp/james_blog_html:/var/www/html/ \
		dding/apache

stop:
	@echo "Stop Docker Container"
	@docker stop jekyll_static_website


clean:
	@echo "Clean Docker Image for this repository"
	@rm -rf /tmp/james_blog_html
	@docker rmi dding/jekyll dding/apache

