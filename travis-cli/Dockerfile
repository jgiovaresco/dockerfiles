FROM debian:jessie
MAINTAINER Julien Giovaresco <dev@giovaresco.fr>

RUN apt-get update && DEBIAN_FRONTEND=noninteractive \
	apt-get install -y ruby-full make git g++ --no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

RUN gem install --no-rdoc --no-ri  -v2.3.8 addressable \
	&& gem install --no-rdoc --no-ri travis

RUN mkdir /project
WORKDIR /project

ENTRYPOINT ["/usr/local/bin/travis"]
