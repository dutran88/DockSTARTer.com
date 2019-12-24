# QBittorrentVPN

qBittorrent is a bittorrent client programmed in C++ / Qt that uses libtorrent (sometimes called libtorrent-rasterbar) by Arvid Norberg. It aims to be a good alternative to all other bittorrent clients out there. qBittorrent is fast, stable and provides unicode support as well as many features. This Docker image is using the headless configuration with the web frontend enabled, as well as OpenVPN to ensure a secure and private connection to the Internet, including use of iptables to prevent IP leakage when the tunnel is down. Privoxy is also included to allow unfiltered access to index sites, to use Privoxy please point your application at http://:8118.

- App: [[Website](https://www.qbittorrent.org/)] [[App Source](https://github.com/binhex/arch-qbittorrentvpn)]
- Docker Image: [[Docker Hub](https://hub.docker.com/)] [[Image Source](https://hub.docker.com/r/binhex/arch-qbittorrentvpn)]

---