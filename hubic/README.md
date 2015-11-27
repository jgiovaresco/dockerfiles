# HubiC

## Pre-requisite

* Create a directory (~/.hubiC) to save HubiC configuration.

* Create a file (~/.hubiC/.hubicpwd) containing your HubiC password

```
echo "YOUR PASSWORD" > ~/.hubiC/.hubicwd
```

* Create a directory (/hubic) which will be synced with HubiC

## Run HubiC daemon

```
docker run -d \
  -v /etc/localtime:/etc/localtime:ro \
  -v /var/run/dbus:/var/run/dbus \
  -v /var/run/user/$(id -u):/var/run/user/$(id -u) \
  -e DBUS_SESSION_BUS_ADDRESS \
  -v $HOME/.hubiC:/home/user/.config/hubiC \
  -v /hubic:/hubiC \
  --name hubic \
  jgiovaresco/hubic
```

## Run HubiC commands

You can use hubiC cli with a simple script

```
#!/bin/bash

docker exec -i hubic /usr/bin/hubic "$@"
```
