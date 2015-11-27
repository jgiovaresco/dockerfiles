# VERSION: 		0.1
# DESCRIPTION:	Create HubiC container (https://hubic.com/fr/telechargements)
# USAGE :
#
#	# Run the container and mount local settings and a directory
#	 docker run -d \
#		-v /etc/localtime:/etc/localtime:ro \
#		-v /var/run/dbus:/var/run/dbus \
#		-v /var/run/user/$(id -u):/var/run/user/$(id -u) \
#		-e DBUS_SESSION_BUS_ADDRESS \
#		-v $HOME/.hubiC:/home/user/.config/hubiC \
#		-v /var/documents:/hubiC \
#		--name hubic \
#		jgiovaresco/hubic

FROM jgiovaresco/debian-with-dockerize:latest
MAINTAINER Julien Giovaresco <dev@giovaresco.fr>

RUN apt-get update && apt-get -y install \
		ca-certificates \
		curl \
		dbus \
		mono-runtime \
		libmono-sqlite4.0-cil \
		libmono-system-core4.0-cil \
		libmono-system-data4.0-cil \
		libmono-system-data-datasetextensions4.0-cil \
		libmono-system-drawing4.0-cil \
		libmono-system-runtime-serialization4.0-cil \
		libmono-system-xml-linq4.0-cil \
		--no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

ENV HUBIC_VERSION 2.1.0
ENV HUBIC_VERSION_MINOR 53
ENV HUBIC_PACKAGE_URL http://mir7.ovh.net/ovh-applications/hubic/hubiC-Linux/${HUBIC_VERSION}/hubiC-Linux-${HUBIC_VERSION}.${HUBIC_VERSION_MINOR}-linux.deb

RUN curl -sSL ${HUBIC_PACKAGE_URL} -o /tmp/hubic.deb \
		&& DEBIAN_FRONTEND=noninteractive dpkg -i /tmp/hubic.deb \
		&& rm -v /tmp/hubic.deb

ENV HOME /home/user
RUN useradd --create-home --home-dir $HOME user \
	&& mkdir $HOME/.config \
	&& chown -R user:user $HOME

VOLUME ["/hubiC"]

USER user
WORKDIR $HOME

CMD ["/usr/lib/hubic/hubic-service"]
