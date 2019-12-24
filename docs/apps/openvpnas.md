# OpenVPN-AS

Openvpn-as is a full featured secure network tunneling VPN software solution that integrates OpenVPN server capabilities, enterprise management capabilities, simplified OpenVPN Connect UI, and OpenVPN Client software packages that accommodate Windows, MAC, Linux, Android, and iOS environments. OpenVPN Access Server supports a wide range of configurations, including secure and granular remote access to internal network and/ or private cloud network resources and applications with fine-grained access control.

- App: [[Website]([http://apps-website](https://openvpn.net/vpn-server/))] [[App Source]([http://github-for-the-app](https://github.com/linuxserver/docker-openvpn-as))]
- Docker Image: [[Docker Hub](https://hub.docker.com/)] [Image Source](https://hub.docker.com/r/linuxserver/openvpn-as/)

---

## Setting up the application

The admin interface is available at `https://<ip>:943/admin` with a default user/password of admin/password

During first login, make sure that the "Authentication" in the webui is set to "Local" instead of "PAM". Then set up the user accounts with their password (user accounts created under PAM do not survive container update or recreation).

The "admin" account is a system (PAM) account and after container update or recreation, its password reverts back to the default. It is highly recommended to block this user's access for security reasons:

1. Set another user as an admin,
1. Delete the "admin" user in the gui,
1. Modify the as.conf file under config/etc and replace the line boot_pam_users.0=admin with #boot_pam_users.0=admin (this only has to be done once and will survive container recreation)

## Server Network Settings

Make sure to change Hostname or IP Address to your public IP or public DNS name.  It defaults to the docker internal IP.  Also, and I think this goes without saying, make sure to forward the correct ports on your firewall to your host IP.

## LetsEncrypt Subdomain Config

[Sample LetsEncrypt Config Here](https://pastebin.com/kMQ7f70f)
