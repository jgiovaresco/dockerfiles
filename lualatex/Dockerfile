# 
# docker run -it --rm=true \
# 		-e USER=$USER -e USERID=$UID \		# bind user for file permissions
#		-v $HOME:/data \
#		--name lualatex jgiovaresco/lualatex
# 

FROM debian:jessie
MAINTAINER Julien Giovaresco <dev@giovaresco.fr>

RUN sed -i 's/main/main contrib non-free/g' /etc/apt/sources.list

RUN apt-get update && apt-get install -y --no-install-recommends \
	texlive \
	texlive-generic-recommended \
	texlive-latex-recommended \
	texlive-fonts-recommended \
	texlive-extra-utils \
	texlive-font-utils \
	texlive-xetex \
	texlive-luatex \
	fonts-lmodern \
	fonts-font-awesome \
	&& apt-get autoclean -y \
	&& apt-get clean -y \
	&& rm -rf /var/lib/apt/lists/* 

RUN useradd lualatex \
	&& mkdir /home/lualatex \
	&& chown lualatex:lualatex /home/lualatex \
	&& mkdir /data \
	&& chown lualatex:lualatex /data

USER lualatex
WORKDIR /data

ENTRYPOINT [ "lualatex" ]
CMD [""]