![image](https://github.com/exedox/synology-setup/assets/55308770/1d8c4e69-33f9-4d80-a495-233f78293c73);.# Synology Setup

This repo is referencing what I did to get things working on my DS918+. It'll be about setting up the network and docker stuff.  I'll reference other guides I found useful.

## Table of Contents
* [Prerequisites](#Prerequisites)
* [Reverse Proxy,Domain,Subdomains](https://github.com/exedox/synology-setup/blob/main/Reverse%20Proxy%2CDomain%2CSubdomain/setup.md)
* [Dockers Used][#Dockers Used)
* [Troubleshooting](#Troubleshooting)

## Prerequisites

* Cloudflare credentials and DNS records set up
* Ports 443 and 80 forwarded
* Commandline access to NAS
* Domain name

## Dockers Used

*  Media: Sonarr, Overseer, Requestrr, Prowlarr
*  Utility: Portainerr, Home Assistant, Bitwarden
*  Downloader: Qbittorrent

## Troubleshooting

* If swag container for wildcard gets a failed to connect error.
   1. Try to ping it to see if there's network connection from connector:
    ```
    curl -i https://api.zerossl.com/acme/eab-credentials-email --data email
    ```
  2. Likely a network issue, turn off pi-hole and see firewall rules of router and synology.
