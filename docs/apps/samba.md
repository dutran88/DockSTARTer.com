# Samba

Samba is a free software re-implementation of the SMB networking protocol, and was originally developed by Andrew Tridgell. Samba provides file and print services for various Microsoft Windows clients and can integrate with a Microsoft Windows Server domain, either as a Domain Controller or as a domain member.

- App: [[Website](https://www.samba.org/)] [[App Source](https://github.com/dperson/samba)]
- Docker Image: [[Docker Hub](https://hub.docker.com/)] [[Image Source](hhttps://hub.docker.com/r/dperson/samba/dockerfile)]

---

Samba is using the `SMB` protocol to share Linux mounts, which then are accessible and mountable on e.g. a Windows computer.

By default, Samba will share all media directories and Docker config directory over SMB on the host. These shares are protected with username `ds` and password `ds`.


## Access Shares

Replace `host` with your DNS or IP-address of your Docker host.

* `\\host\DockSTARTer`

## Related

### Mounting Windows share in Linux

See [SMB Mounting](https://dockstarter.com/advanced/smb-mounting/).
