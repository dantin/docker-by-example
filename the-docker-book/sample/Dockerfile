FROM ubuntu:16.04

ENV REFRESH_AT 2018-05-30

ADD yum/sources.list /etc/apt/sources.list

RUN apt-get -yqq update; apt-get -yqq install nginx
RUN mkdir -p /var/www/html/website

ADD nginx/global.conf /etc/nginx/conf.d/
ADD nginx/nginx.conf  /etc/nginx/nginx.conf

EXPOSE 80
