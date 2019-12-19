# NextCloud

Nextcloud gives you access to all your files wherever you are.
Where are your photos and documents? With Nextcloud you pick a server of your choice, at home, in a data center or at a provider. And that is where your files will be. Nextcloud runs on that server, protecting your data and giving you access from your desktop or mobile devices. Through Nextcloud you also access, sync and share your existing data on that FTP drive at the office, a Dropbox or a NAS you have at home.

- App: [[Website](https://nextcloud.com/)] [[App Source](http://github-for-the-app)]
- Docker Image: [[Docker Hub](https://hub.docker.com/)] [[Image Source](https://hub.docker.com/r/linuxserver/nextcloud)]

---

If you are running the DockSTARTer Nextcloud container behind a LetsEncrypt Reverse gateway, you may need to add a extra line to the NextCloud config.php file so it can find it.

you will be able to access the web page all OK, but any apps may timeout or return an invalid password

run the below command and add the line to the the config.php file before the );

```bash
nano /config/www/nextcloud/config/config.php

'overwritehost' => 'hostname',
```

where your 'hostname' is the URL you use to access your NextCloud web interface, make sure you include the comma at the end.

this will allow the apps to pass the username/password through to the application
