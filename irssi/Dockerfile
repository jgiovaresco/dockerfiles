# VERSION:		0.1
# DESCRIPTION:	IRSSI docker container with urxvt-256-color support
# AUTHOR:		Julien Giovaresco <dev@giovaresco.fr>
# USAGE:
#	docker run --rm -it \
#		-v /etc/localtime:/etc/localtime:ro \
#		-v /etc/machine-id:/etc/machine-id:ro \
#		-v /var/run/dbus:/var/run/dbus \
#		-v /var/run/user/$(id -u):/var/run/user/$(id -u) \
#		-e TERM \
#		-e XAUTHORITY \
#		-e DBUS_SESSION_BUS_ADDRESS \
#		-e HOME \
#		-v /etc/passwd:/etc/passwd:ro \
#		-v /etc/group:/etc/group:ro \
#		-u $(whoami) -w "$HOME" \
#		-v $HOME/.Xauthority:$HOME/.Xauthority \
#		-v $HOME/.irssi:$HOME/.irssi \
#		--read-only \
#		--name irssi \
#		jgiovaresco/irssi
FROM jess/irssi

USER root

RUN apt-get update && apt-get install -y --no-install-recommends \
		ncurses-term \
	&& rm -rf /var/lib/apt/lists/*

USER user
