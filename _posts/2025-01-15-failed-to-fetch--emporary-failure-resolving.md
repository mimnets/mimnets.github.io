---
title: Failed to fetch....Temporary failure resolving 'iad-ad-3.clouds.ports.ubuntu.com'
date: 2025-01-15 07:12:05 +/-TTTT
categories: ["Tech", "Solutions"]
tags: ["ubuntu", "linux"]     # TAG names should always be lowercase
description: The error message you're encountering, "Temporary failure resolving 'iad-ad-3.clouds.ports.ubuntu.com'," indicates a DNS resolution issue.
---

- Failed to fetch http://iad-ad-3.clouds.ports.ubuntu.com/ubuntu-ports/pool/main/n/network-manager-pptp/network-manager-pptp_1.2.8-2_arm64.deb  Temporary failure resolving 'iad-ad-3.clouds.ports.ubuntu.com'
  - On my ubuntu 20:04 server hosted on OCI Cloud

The error message you're encountering, "Temporary failure resolving 'iad-ad-3.clouds.ports.ubuntu.com'," indicates a DNS resolution issue. This means your system is unable to resolve the domain name into an IP address, which is necessary for accessing the repository and downloading packages. Here are some steps you can take to troubleshoot and potentially resolve this issue on Ubuntu 20.04:
1. Check Internet Connection
Ensure your internet connection is stable and working properly. Try accessing other websites or services to confirm.
2. DNS Server Configuration
Check DNS Settings: Ensure that your DNS settings are correct. You can try using a public DNS service like Google's DNS (8.8.8.8) or Cloudflare's DNS (1.1.1.1).

```
sudo nano /etc/resolv.conf

```

Add or modify the following lines:

```
nameserver 8.8.8.8
nameserver 1.1.1.1
```

Restart Networking Service: After changing DNS settings, restart the networking service.
```
sudo systemctl restart networking
```

3. Check for Firewall or Proxy Issues
  - Ensure that your firewall or proxy settings are not blocking the connection to the Ubuntu repositories.
1. Try a Different Repository
  - If the issue persists, try using a different Ubuntu repository mirror. You can do this by editing your /etc/apt/sources.list file.

```
sudo nano /etc/apt/sources.list
```

- Replace the existing lines with a different mirror, for example:
```
deb http://archive.ubuntu.com/ubuntu focal main restricted
deb http://archive.ubuntu.com/ubuntu focal-updates main restricted
deb http://archive.ubuntu.com/ubuntu focal universe
deb http://archive.ubuntu.com/ubuntu focal-updates universe
deb http://archive.ubuntu.com/ubuntu focal multiverse
deb http://archive.ubuntu.com/ubuntu focal-updates multiverse
```

5. Update and Clean APT Cache
  - After making changes, update and clean the APT cache.
```
sudo apt update
sudo apt clean
sudo apt autoclean
```
6. Check for System Updates
  - Ensure your system is up-to-date.
```
sudo apt update && sudo apt upgrade -y
```

If none of these steps resolve the issue, it might be a temporary problem with the Ubuntu repository server or your local network configuration. You can try again later or seek further assistance from your network administrator or ISP.
