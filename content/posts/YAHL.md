---
title: "Yet Another Home Lab (YAHL)"
date: 2024-12-23T14:29:42+01:00
draft: false
toc: false
images:
tags:
  - blog
---
## Introduction
I figured now being the holidays a good a time as any to document my HomeLab environment. Ever since relocating to the Netherlands I've had to completely rebuild my homelab. I've done things in a much more modern and frankly maintainable fashion
Currently everything is still fairly simple with little to no automation. Rushed to get critical servrices up and running. I'm hoping to change that in the coming months.

## Hardware
  I opted for something small but with enough power to host my services. I have two servers, one for running my main services and the other for storage and kubernetes playground.

### evergiven-1
  Main host which runs all my services.
- AsRock Deskmini x300 Barebones Kit
- Ryzen 5 5600G
- 64GB DDR4
- 2x 2TB NVMe
### evergiven-2
  Storage and Kubernetes playground.
- AsRock DeskMeet X300 Barebones Kit
- Ryzen 5 5600G
- 32GB DDR4
- 1x 1TB NVMe
- 1x 6TB WD Red HDD

## Network
Currently I have a single Mikrotik switch which is more than enough for my needs. I have a 4Gbps fiber connection from KPN which has been great. I've been able to get the full 4Gbps symmetrical on the Mikrotik Switch. So far the network map is fairly flat. I do plan on segregating home devices from the lab devices in the future.
### Hardware
- Mikrotik CRS310-8G+2S+IN
- KPN Router w/ 4Gbps Uplink

## Services
This isn't an exhaustive list of services but the main ones I am running.
- Jellyfin
- Paaster
- Jetlog
- Grafana
- Portainer
- Nginx-Proxy-Manager

## Service map
[![Service Map](/netmap.webp)](/netmap.webp)
## evergiven-1
### OS
- Ubuntu 24.04
### Services
- Jellyfin\
  Running Jellyfin for my media needs. I've been using Jellyfin for a few years now, I've disliked Plex's direction and Jellyfin has been a great open source alternative.
- Paaster\
  My own pastebin service. Only recently started using it but it's been a great way to share code snippets and other text with friends.
- Jetlog\
  Flight tracking sercice I deployed since App-In-The-Air was discontinued. It's still missing some key features but I've been able to track my flights with ease. Currently looking into implementing TZ support for flights.
- Grafana\
  Monitoring service for all my services. Grafana is definitely the go-to for monitoring services. Recently started monitoring network traffic with mikrotik through SNMP.
- Portainer\
  Docker management service. Opted for portainer since it's simple and easy to use
- Nginx-Proxy-Manager\
  Reverse proxy service. Only recently adopted this with the new Homelab. At the core of my entire setup. It's been great for managing all my services and setting up SSL with Let's Encrypt.

## evergiven-2
### OS
- Ubuntu 24.04
### Services
- Kubernetes[^1]\
  Currently running a single node kubernetes cluster. I've been wanting to learn more about kubernetes and this has been a great way to do so.
- NFS\
  Network File System for sharing files between my two servers. Ideally this wouldn't be through NFS but the drive was orginally in a Windows machine and I didn't feel like reformatting it.

## Future Plans
- Automate the deployment of services
- Implement a CI/CD pipeline
- Implement a backup solution
- Re-implement a VPN service
- Re-implement a web-interface for the NFS share
- Maybe migrate docker services to kubernetes

[^1]: I am also running some privately services in development that aren't ready for public use. I am just internally using them and testing. Some of which may never see the light of day.
