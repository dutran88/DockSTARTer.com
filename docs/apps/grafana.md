# Grafana

Description sentence(s).

- App: [[Website](https://grafana.com/)] [[App Source](https://github.com/grafana/grafana)]
- Docker Image: [[Docker Hub](https://hub.docker.com/)] [[Image Source](https://hub.docker.com/r/grafana/grafana/)]

---

## Fix for permission problems

If you see the following error:

```
mkdir: cannot create directory '/var/lib/grafana/plugins': Permission denied,
GF_PATHS_DATA='/var/lib/grafana' is not writable.
```

Run the following command to fix it:

`sudo chown -R $USER:$USER ~/.config/appdata/grafana`
