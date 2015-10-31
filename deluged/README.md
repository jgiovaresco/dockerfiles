
# deluged

## Pre-requisite

Create a directory (``/config``) to save Deluge configuration.

Create a directory (``/downloads``) containing following sub-directories : 

* __complete__ : directory where completed downloads are stored
* __incoming__ : directory in which currently downloaded data is saved
* __queue__ : directory where torrent files will be recognized and auto-loaded
* __torrents__ : directory where temporary files are stored

## Run deluged

The container needs some environment variables

* __ADMIN_NAME__ : login used to authenticate user in the web interface
* __ADMIN_PASSWORD__ : password used to authenticate user in the web interface

```
docker run -d -p 58846:58846 -v /config:/config -v /downloads:/downloads  -e ADMIN_NAME=admin -e ADMIN_PASSWORD=admin --name deluged jgiovaresco/deluged
```