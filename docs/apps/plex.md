# Plex

Plex organizes video, music and photos from personal media libraries and streams them to smart TVs, streaming boxes and mobile devices. This container is packaged as a standalone Plex Media Server. has always been a top priority. Straightforward design and bulk actions mean getting things done faster.

- App: [[Website](https://plex.tv/)] [[App Source](https://github.com/linuxserver/docker-plex)]
- Docker Image: [[Docker Hub](https://hub.docker.com/)] [[Image Source](https://hub.docker.com/r/linuxserver/plex/)]

---

## Cannot Setup Server On First Run

Upon starting up Plex for the first time, it's very likely you'll need to follow these steps:

Edit `~/.docker/compose/.env` and set `PLEX_NETWORK_MODE=host`. After claiming your server set `PLEX_NETWORK_MODE=` (back to blank).

## How To Run Plex Pass Versions

Edit `~/.docker/compose/.env` and set:

```bash
PLEX_VERSION=plexpass
```

Then run `ds -c`

## Rebuilding From Scratch

Thankfully, some of this information is well documented (but not easily found) over on Plex's website here!

1. Moving an installation to another system: [https://support.plex.tv/articles/201370363-move-an-install-to-another-system/](https://support.plex.tv/articles/201370363-move-an-install-to-another-system/)
1. Where is the Plex Media Server data directory? [https://support.plex.tv/articles/202915258-where-is-the-plex-media-server-data-directory-located/](https://support.plex.tv/articles/202915258-where-is-the-plex-media-server-data-directory-located/)

## Hardware Transcoding

If you would like to have Plex use a GPU that is attached to your DockSTARTer host, you can do this using an override like so:

```yaml
  plex:
    devices:
      - /dev/dri:/dev/dri
```

Refer to this forum post for details: [Using Hardware Acceleration in Docker](https://forums.plex.tv/t/using-hardware-acceleration-in-docker/229702/3)
