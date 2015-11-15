FROM debian:jessie
MAINTAINER Julien Giovaresco <dev@giovaresco.fr>

RUN sed -i 's/main/main contrib non-free/g' /etc/apt/sources.list

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update \
	&& apt-get install -y --no-install-recommends wget \
			locales \
	&& apt-get autoclean -y \
	&& apt-get clean -y \
	&& rm -rf /var/lib/apt/lists/* 

RUN DEBIAN_FRONTEND=noninteractive \
		&& echo "en_US.UTF-8 UTF-8" > /etc/locale.gen \
		&& locale-gen 

ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
ENV LC_ALL en_US.UTF-8

RUN wget --no-check-certificate https://github.com/jwilder/dockerize/releases/download/v0.0.2/dockerize-linux-amd64-v0.0.2.tar.gz \
	&& tar -C /usr/local/bin -xzvf dockerize-linux-amd64-v0.0.2.tar.gz \
	&& rm -f dockerize-linux-amd64-v0.0.2.tar.gz
