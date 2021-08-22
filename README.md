# Spotify Daemon in Docker
[![Build Status](https://drone.ch1.ninja/api/badges/Ch1ch1/docker-spotifyd/status.svg)](https://drone.ch1.ninja/Ch1ch1/docker-spotifyd)
![spotifyd%20version](https://img.shields.io/badge/spotifyd%20version-0.3.2-green)

Spotifyd within a docker container for x64 architectures
Alsa for audio-backend with D-Bus API for controlling spotifyd through generic media players.

Docker-compose:
```
version: '3'
services:
  spotifyd:
    image: ch1ch1/docker-spotifyd:alsa-dbus
    network_mode: host
    devices:
      - /dev/snd:/dev/snd
    volumes:
      - /usr/share/alsa:/usr/share/alsa
      - /etc/spotifyd/spotifyd.conf:/etc/spotifyd.conf
      - /etc/asound.conf:/etc/asound.conf
    group_add:
      - ${AUDIO_GRP}
```

Replace ${AUDIO_GRP} with the audio group number of your system.

## Limitations
Spotifyd requires a Spotify Premium account.

## Acknowledgements
All credit goes to [spotifyd](https://github.com/Spotifyd/spotifyd). The instructions, dockerfile and explanation at [GnaphronG/docker-spotifyd](https://github.com/GnaphronG/docker-spotifyd) consititute a major portion of the contents in this repository.
