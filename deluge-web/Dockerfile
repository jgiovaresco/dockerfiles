FROM jgiovaresco/debian-with-dockerize:latest
MAINTAINER Julien Giovaresco <dev@giovaresco.fr>

RUN apt-get update \
	&& apt-get install -y --no-install-recommends deluge-web \
	&& rm -rf /var/lib/apt/lists/* 

RUN groupadd --gid 1002 downloads \
	&& useradd --gid downloads deluge \
	&& mkdir /var/log/deluge \
	&& chown deluge:downloads /var/log/deluge

USER deluge

EXPOSE 8112

VOLUME ["/config"]

ADD web.conf /home/deluge/web.conf

CMD dockerize \
		-template /home/deluge/web.conf:/config/web.conf \
		-stdout /var/log/deluge/deluge.log \
		deluge-web --config /config -l /var/log/deluge/deluge.log -L warning