# Variable Information 

This is page is to explain each variable inside .env file. We'll break it down in three parts.

### - Global Settings
### - Backup Settings
### - VPN Settings

---

## Global Settings

<b>Global settings</b>: are the settings that apply to the local server and set initial default values for all virtual hosts running on this server.

<b>COMPOSE_HTTP_TIMEOUT=60</b>: Configures the time (in seconds) a request to the Docker daemon is allowed to hang before Compose considers it failed. Defaults to 60 seconds.

<b>DOCKERCONFDIR</b>: Your default application config files are stored. 

<b>DOCKERGID</b>: Docker group name

<b>DOCKERHOSTNAME</b>: Label that is assigned to a device connected to a computer network and that is used to identify the device. We recommend using your local host name when you installed your server. 

<b>Docker Logs</b> :
Docker includes multiple logging mechanisms to help you get information from running containers and services. These mechanisms are called logging drivers.

Each Docker daemon has a default logging driver, which each container uses unless you configure it to use a different logging driver.

In addition to using the logging drivers included with Docker, you can also implement and use logging driver plugins.

- <b>DOCKERLOGGING_MAXFILE</b>: The maximum number of log files that can be present. If rolling the logs creates excess files, the oldest file is removed. Only effective when max-size is also set. A positive integer. Defaults to 1.
- <b>DOCKERLOGGING_MAXSIZE</b>: The maximum size of the log before it is rolled. A positive integer plus a modifier representing the unit of measure (k, m, or g). Defaults to -1 (unlimited).

<b>DOCKERSHAREDDIR</b>: To share files between a host system and the Docker container.

<b>MEDIADIR_</b>: To share media files between a host system and the Docker container.

- AUDIOBOOKS
- BOOKS
- COMICS
- MOVIES
- MUSIC
- TV

<b>PGID & PUID</b>: Allows our containers to map the container's internal user to a user on the host machine


<b>TZ</b>: Time Zone Database. The Time Zone Database (often called tz or zoneinfo) contains code and data that represent the history of local time for many representative locations around the globe.

---

Environment Example

- You can find your environment file inside ~/.docker/compose/.env 

```yaml
# Global Settings
COMPOSE_HTTP_TIMEOUT=60 
DOCKERCONFDIR=~/.config/appdata
DOCKERGID=999
DOCKERHOSTNAME=DockSTARTer
DOCKERLOGGING_MAXFILE=10
DOCKERLOGGING_MAXSIZE=200k
DOCKERSHAREDDIR=~/.config/appdata/shared
DOWNLOADSDIR=/mnt/downloads
MEDIADIR_AUDIOBOOKS=/mnt/medialibrary/audiobooks
MEDIADIR_BOOKS=/mnt/medialibrary/books
MEDIADIR_COMICS=/mnt/medialibrary/comics
MEDIADIR_MOVIES=/mnt/medialibrary/movies
MEDIADIR_MUSIC=/mnt/medialibrary/music
MEDIADIR_TV=/mnt/medialibrary/tv
PGID=1000
PUID=1000
TZ=America/Chicago
```

---

## VPN Settings 

```yaml
# VPN Settings
LAN_NETWORK=192.168.x.x/24
NS1=1.1.1.1
NS2=8.8.8.8
VPN_ENABLE=yes
VPN_OPTIONS=
VPN_OVPNDIR=~/.config/appdata/.openvpn
VPN_PASS=
VPN_PROV=custom
VPN_USER=

# END OF DEFAULT SETTINGS
```

