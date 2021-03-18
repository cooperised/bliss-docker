# bliss-docker

A repository for creating a docker container including bliss (https://www.blisshq.com)

![docker pulls](https://img.shields.io/docker/pulls/romancin/bliss.svg) ![docker stars](https://img.shields.io/docker/stars/romancin/bliss.svg) [![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=X2CT2SWQCP74U)

Latest versions:

![Docker Image Version (latest semver)](https://img.shields.io/docker/v/romancin/bliss) ![docker size](https://img.shields.io/docker/image-size/romancin/bliss) 

You can invite me a beer if you want ;) 

This is a completely funcional Docker image with Bliss HQ.

Based on Alpine Linux, which provides a very small size. 

Tested and working on Synology and QNAP, but should work on any x86_64 devices.

Instructions: 
- Map any local port to 3220 for web access
- Map any local port to 3221 (used for bliss internal web server)
- Map a local volume to /config (Stores configuration data)
- Map a local volume to /music (This is the directory wher you should put your music for bliss to scan)

NOTE: In order to migrate from the old container, you need to enter the local directory you are mapping to /config, create a ".bliss" directory on it and move all files and directories to this directory. This container fixes persitent data. With the older container it didn't work.

Sample run command:

```bash
docker run -d --name=bliss \
-v /share/Container/bliss:/config \
-v /share/MyMusic:/music \
-e PGID=0 -e PUID=0 \
-e TZ=Europe/Madrid \
-p 3220:3220 \
-p 3221:3221 \
romancin/bliss:latest
```
