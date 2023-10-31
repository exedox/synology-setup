# Synology Setup

This repo is referencing what I did to get things working on my DS918+. It'll be about setting up the network and docker stuff.  I'll reference other guides I found useful.

## Table of Contents
* [Prerequisites](#Prerequisites)
* [Reverse Proxy,Domain,Subdomains](#Reverse-Proxy,Domain,Subdomains)

## Prerequisites

* Cloudflare credentials and DNS records set up
* Ports 443 and 80 forwarded
* Commandline access to NAS
* Domain name

## Reverse Proxy,Domain,Subdomains

 1. Follow [mariushosting](https://mariushosting.com) for the a lot of good info for synology set up. The following will provide steps for setting up using synology's domain.
      a. This is the easy method using synology's DDNS because it takes care of everything.
      b. [DDNS Setup](https://mariushosting.com/synology-difference-between-quickconnect-and-ddns/)
      c. [Reverse Proxy](https://mariushosting.com/synology-how-to-use-reverse-proxy-on-dsm-7/)

 3.  Using custom domain with cloudflare:
    
      a. Get custom domain, ex. [namecheap](https://www.namecheap.com).
      b. Manage domain and copy/paste [cloudflare nameserver](https://developers.cloudflare.com/automatic-platform-optimization/get-started/change-nameservers).
     ![image](https://github.com/exedox/synology-setup/blob/main/images/nameserver.PNG)
