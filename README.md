# Docker PiHole + DNSCrypt

This repository contains a working docker configuration for pihole and dnscrypt that support DoH.

## How to setup

First of all, you need a raspberry pi. Set a static ip on it and connect it to your router.

- Set in your router the raspberry ip address as DNS ip. 
- Install [docker](https://docs.docker.com/engine/install/raspberry-pi-os/).
- Install portainer to get a cool UI of your dockers status (optional):
    ```bash
    sudo docker run -d -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
    ```
- Create a new directory ```config_pihole``` on your home folder (pi by default ```~```) and get in.
- Pull this repo.
- Change network details and pihole password in ```.env``` if needed.
    > The ```.env``` file contains the ip addresses of containers in docker. You should not modify it if not specially needed.
- Run this:
    ```bash
    sudo docker compose up -d
    ```
- It should work :).

## ```.env``` file explanation

These 4 fields should not be modified if you don't have specific configuration: 
- ```SUBNET```: arbitrary subnet for Pihole and DNSCrypt.
- ```GATEWAY```: gateway of your ```SUBNET```.
- ```DNSCRYPT_IP```: ip from ```SUBNET``` assigned to DNSCrypt docker.
- ```PIHOLE_IP```: ip from ```SUBNET``` assigned to Pihole docker.

- ```RASPBERRY_IP```: real ip of your raspberry in your physical network. This setting is used in docker config of your pihole to match UI portal ip with the physical raspberry ip to avoid 403 error. 
- ```PIHOLE_PASSWORD```: password of pihole portal.

## Advanced settings

You can modify as your own the dnscrypt settings in ```dnscrypt/dnscrypt-proxy.toml```.
By default it use mullvad DoH as DNS provider and listen in docker with port 5053.

## Pihole blocklists

You can check the ```blocklists.txt``` file that contains some cool blocklists from the web.
