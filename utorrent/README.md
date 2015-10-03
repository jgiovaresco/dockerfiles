
# µtorrent

## Pre-requisite

Create a directory (``/downloads``) containing following sub-directories : 

* __complete __ : directory where completed downloads are stored
* __incoming__ : directory in which currently downloaded data is saved
* __queue__ : directory where torrent files will be recognized and auto-loaded
* __temp_files__ : directory where temporary files are stored
* __torrent_files__ : directory where torrent files are stored

## Run µtorrent

The container needs some environment variables

* __WEBUI_PORT__ : port of the web interface
* __ADMIN_NAME__ : login used to authenticate user in the web interface
* __ADMIN_PASSWORD__ : password used to authenticate user in the web interface

```
docker run -d -p 8080:8080 -v /downloads:/data -e WEBUI_PORT=8080 -e ADMIN_NAME=admin -e ADMIN_PASSWORD=admin --name utorrent jgiovaresco/utorrent
```