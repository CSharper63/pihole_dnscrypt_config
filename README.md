# Docker PiHole + DNSCrypt

This repository contains a working docker configuration for pihole and dnscrypt that support DoH.

## How to setup

First of all, you need a raspberry pi. Set a static ip on it and connect it to your router.

- Set in your router the raspberry ip address as DNS ip. 
- Install [docker](https://docs.docker.com/engine/install/raspberry-pi-os/).
- Create a new directory ```config_pihole``` on your home folder (pi by default ```~```)
- Pull this repo.
- Change network details and pihole password in ```.env``` if needed.
- Run ```sudo docker compose up -d```
- It should work :).


## Advanced settings

You can modify as your own the dnscrypt settings in ```dnscrypt/dnscrypt-proxy.toml```.
By default it use mullvad DoH as DNS provider and listen in docker with port 5053.

## Pihole blocklists

You can check the ```blocklists.txt``` file that contains some cool blocklists from the web.
