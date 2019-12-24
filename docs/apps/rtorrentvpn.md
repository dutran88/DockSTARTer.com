# rTorrentVPN

rTorrent is a quick and efficient BitTorrent client that uses, and is in development alongside, the libTorrent (not to be confused with libtorrent-rasterbar) library. It is written in C++ and uses the ncurses programming library, which means it uses a text user interface. When combined with a terminal multiplexer (e.g. GNU Screen or Tmux) and Secure Shell, it becomes a convenient remote BitTorrent client. This Docker image includes the popular ruTorrent web frontend to rTorrent for ease of use, as well as OpenVPN to ensure a secure and private connection to the Internet, including use of iptables to prevent IP leakage when the tunnel is down. Privoxy is also included to allow unfiltered access to index sites, to use Privoxy please point your application at http://:8118.

- App: [[Website](http://apps-website)] [[App Source](https://github.com/binhex/arch-rtorrentvpn)]
- Docker Image: [[Docker Hub](https://hub.docker.com/)] [[Image Source](https://hub.docker.com/r/binhex/arch-rtorrentvpn/dockerfile)]

---