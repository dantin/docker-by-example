#
# Makefile for Tomcat
#
# version 1.0 2018-06-05
#

.PHONY: build clean start stop


default: build


build:
	@echo "Build Fetcher Image"
	@cd fetcher; docker build -t dding/fetcher .
	@echo "Build Tomcat Image"
	@cd tomcat7; docker build -t dding/tomcat7 .


download: 
	@echo "Download 'sample.war'"
	@docker run -t -i --name sample \
		dding/fetcher \
		https://tomcat.apache.org/tomcat-7.0-doc/appdev/sample/sample.war


start: 
	@echo "Start Tomcat7 Continer"
	@docker run --name sample_app \
		--volumes-from sample \
		-d -P dding/tomcat7


stop:
	@echo "Stop Docker Container"
	@docker stop sample_app


clean:
	@echo "Clean Docker Image for this repository"
	@docker rm $(shell docker ps -a -q --filter name="sample|sample_ap")
	@echo "Clean Docker Volume"
	@docker volume prune -f

