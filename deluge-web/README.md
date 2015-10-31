
# deluge-web

## Pre-requisite

Create a directory (``/config``) to save Deluge configuration.

A container based on image ``jgiovaresco/deluged`` must be running before starting a container based on this image.

## Run deluged

```
docker run -d -p 8112:8112 -v /config:/config --link deluged --name deluge-web jgiovaresco/deluge-web
```