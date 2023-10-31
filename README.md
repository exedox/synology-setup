# Synology Setup

This repo is referencing what I did to get things working on my DS918+. It'll be about setting up the network and docker stuff.  I'll reference other guides I found useful.

## Table of Contents
* [Prerequisites](#Prerequisites)
* [Reverse Proxy,Domain,Subdomains](#Reverse-Proxy,Domain,Subdomains)
* [Troubleshooting](#Troubleshooting)

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

      c. Use [this](https://github.com/mrikirill/SynologyDDNSCloudflareMultidomain) to add cloudflare to synology DDNS options. Make following changes
     
        * Under DNS settings, instead of device ip, use [external ip](https://whatismyipaddress.com/) for ipaddress
     
        * When editing DDNS.  In the hostname section only included the domain.com. We will create a wildcard because that's more convenient than creating several individual SSL certificates.
             ![image](https://github.com/exedox/synology-setup/blob/main/images/hostname.PNG)
     d. Set up A Record and CName on cloudflare:
        * Can set things up proxied for subdomains after obtaining SSL, but leave plex or emby as dns only because if you orange them, it breaks the rules.  Keep proxy greyed until SSL is created.
          [image](https://github.com/exedox/synology-setup/blob/main/images/arecord.PNG)

   4.  Create Wildcard SSL Certificate for subdomain
      
      a. Create certbot using [linuxserver docker](https://docs.linuxserver.io/general/swag/#create-container-via-dns-validation-with-a-wildcard-cert), no need to expose ports.
      
      b. Edit dns-conf/cloudflare.ini:
      
      ```
      dns_cloudflare_email = youremailaddress@protonmail.com
      dns_cloudflare_api_key = yourglobalapikey
      ```
