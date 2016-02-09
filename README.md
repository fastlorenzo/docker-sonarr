# Docker Sonarr (previously NzbDrone)

### Building
docker build -t sonarr .


### Ports
- **TCP 8989** - Web Interface (HTTP)
- **TCP 9898** - Web Interface (HTTPS)

### Volumes
- **/volumes/config** - Sonarr configuration data
- **/volumes/completed** - Completed downloads from download client
- **/volumes/media** - Sonarr media folder

Added user sonarr / group sonarr (UID/GID : 1023)

When mounting volumes from the host, ensure this uid has the correct permission on the folders.

## Running

The quickest way to get it running without integrating with a download client or media server (plex)
```
sudo docker run --restart always --name sonarr -p 8989:8989/tcp -p 9898:9898/tcp --net:host -v /path/to/your/media/folder/:/volumes/media -v /path/to/your/completed/downloads:/volumes/completed tuxeh/sonarr
```
