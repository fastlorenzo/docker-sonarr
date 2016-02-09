# Docker Sonarr (previously NzbDrone)

### Tags
- tuxeh/sonarr:**latest** - Installs from Sonarr master repository
- tuxeh/sonarr:**develop** - Installs from Sonarr develop repository

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
sudo docker run --restart always --name sonarr -p 8989:8989 -p 9898:9898 --net:host -v /path/to/your/media/folder/:/volumes/media -v /path/to/your/completed/downloads:/volumes/completed tuxeh/sonarr
```

You can link to the download client's volumes and plex using something similar:
```
sudo docker run --restart always --name sonarr --volumes-from plex --link plex:plex --volumes-from deluge --link deluge:deluge -p 8989:8989 tuxeh/sonarr
```

