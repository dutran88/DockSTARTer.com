# HomeAssistant

Open source home automation that puts local control and privacy first. Powered by a worldwide community of tinkerers and DIY enthusiasts. Perfect to run on a Raspberry Pi or a local server.

- App: [[Website](https://www.home-assistant.io/docs/installation/docker/)] [[App Source](http://github-for-the-app)]
- Docker Image: [[Docker Hub](https://hub.docker.com/)] [[Image Source](https://hub.docker.com/r/homeassistant/home-assistant/)]

---

## Environment Variable

You may want to override `homeassistant` with environment variable `PYTHONWARNINGS="ignore:Unverified HTTPS request"` if you recevieve warning each 10 second for e.g. device tracking of self-signed Unifi Controller SSL certificated.

Reference: [https://community.home-assistant.io/t/endless-insecurerequestwarning-errors-with-unifi/31831/12](https://community.home-assistant.io/t/endless-insecurerequestwarning-errors-with-unifi/31831/12)
