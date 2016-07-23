
# Sabnzbd 1.0.3

## Pre-requisite

Create a directory (``/config``) to save Sabnzbd configuration.

Create a directory (``/downloads``) containing following sub-directories :

* __cache__ : directory where cache files are stored
* __complete__ : directory where completed downloads are stored
* __incomplete__ : directory in which currently downloaded data is saved
* __queue__ : directory where NZB files will be recognized and auto-loaded

## Run sabnzbd

```
docker run -it --rm=true -v /config:/config -v /downloads:/downloads -p 8080:8080 --name sabnzbd jgiovaresco/sabnzbd
```
