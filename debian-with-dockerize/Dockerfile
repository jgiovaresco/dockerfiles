FROM debian:jessie
MAINTAINER Julien Giovaresco <dev@giovaresco.fr>

RUN sed -i 's/main/main contrib non-free/g' /etc/apt/sources.list

RUN apt-get update \
	&& apt-get install -y --no-install-recommends wget \
	&& apt-get autoclean -y \
	&& apt-get clean -y \
	&& rm -rf /var/lib/apt/lists/* 

RUN wget --no-check-certificate https://github.com/jwilder/dockerize/releases/download/v0.0.2/dockerize-linux-amd64-v0.0.2.tar.gz \
	&& tar -C /usr/local/bin -xzvf dockerize-linux-amd64-v0.0.2.tar.gz \
	&& rm -f dockerize-linux-amd64-v0.0.2.tar.gz