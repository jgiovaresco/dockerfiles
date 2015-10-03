FROM jgiovaresco/debian-with-dockerize:latest
MAINTAINER Julien Giovaresco <dev@giovaresco.fr>

RUN apt-get update \
	&& apt-get install -y --no-install-recommends libssl1.0.0 \
	&& rm -rf /var/lib/apt/lists/* 

RUN groupadd --gid 1002 downloads \
	&& useradd --home-dir /home/utorrent --gid downloads --create-home utorrent \
	&& mkdir /home/utorrent/conf /data /var/log/utorrent \
	&& chown -R utorrent:downloads /home/utorrent \
	&& chown utorrent:downloads /data \
	&& chown utorrent:downloads /var/log/utorrent 

USER utorrent	
WORKDIR /home/utorrent

ADD utserver.tmpl conf/

RUN wget --no-check-certificate -O utorrent.tar.gz http://download.ap.bittorrent.com/track/beta/endpoint/utserver/os/linux-x64-debian-7-0 \
	&& tar xvfz utorrent.tar.gz && mv utorrent-server-alpha-v3_3 utorrent-server \
	&& rm -rf linux-x64-debian-7-0 utorrent-server/docs utorrent.tar.gz

EXPOSE 6881

VOLUME ["/data"]

CMD dockerize \
		-template /home/utorrent/conf/utserver.tmpl:/home/utorrent/conf/utserver.conf \
		-stdout /var/log/utorrent/utorrent.log \
		/home/utorrent/utorrent-server/utserver \
			-configfile /home/utorrent/conf/utserver.conf \
			-logfile /var/log/utorrent/utorrent.log