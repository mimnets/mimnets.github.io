---
title: NextCloud instalation with Docker
date: 2025-01-28 11:13:05 +/-TTTT
categories: ["Tech", "Solutions"]
tags: ["docker", "linux", "nextcloud"]     # TAG names should always be lowercase
description: Docker Compose code to install nexcloud on docker
---

# Docker Compose code to install nexcloud on docker

## Install Docker and Docker Compose
### Install Docker:
```
sudo apt update
sudo apt install docker.io -y
```
### Install Docker Compose:

```
sudo apt install docker-compose -y
Start and Enable Docker:
```
```
sudo systemctl start docker
sudo systemctl enable docker
```
### Add Your User to the Docker Group (Optional):

```
sudo usermod -aG docker $USER
Log out and back in for this to take effect.
```
1. Install Portainer
Run Portainer Using Docker:
```
docker volume create portainer_data
docker run -d -p 8000:8000 -p 9443:9443 --name portainer \
    --restart=always -v /var/run/docker.sock:/var/run/docker.sock \
    -v portainer_data:/data portainer/portainer-ce:latest
```
Access Portainer:

Open a browser and go to https://<your-server-ip>:9443.
Follow the setup process to create an admin user.

1. Set Up Nextcloud Using Docker Compose in Portainer
Step 1: Create a Docker Compose Stack
Log in to Portainer.
Navigate to Stacks > Add Stack.
Name your stack, e.g., nextcloud-stack.

Step 2: Add the Compose Configuration
Paste the following Docker Compose configuration in the editor:
```
version: '3.8'

services:
  nextcloud:
    image: nextcloud:latest
    container_name: nextcloud
    restart: always
    ports:
      - "8080:80"
    volumes:
      - nextcloud_data:/var/www/html
    environment:
      - MYSQL_HOST=db
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextclouduser
      - MYSQL_PASSWORD=your_password

  db:
    image: mariadb:latest
    container_name: nextcloud_db
    restart: always
    environment:
      - MYSQL_ROOT_PASSWORD=your_root_password
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextclouduser
      - MYSQL_PASSWORD=your_password
    volumes:
      - db_data:/var/lib/mysql

volumes:
  nextcloud_data:
  db_data:
  
  ```
Replace your_password and your_root_password with secure passwords.

Step 3: Deploy the Stack
Click Deploy the Stack.
Portainer will pull the required images and start the containers.

1. Access Nextcloud
Open your browser and navigate to http://<your-server-ip>:8080.

Complete the Nextcloud setup wizard:
```
Database host: db
Database name: nextcloud
Database user: nextclouduser
Database password: your_password
```
6. Secure with HTTPS (Optional)

To secure Nextcloud, you can set up a reverse proxy with Nginx or Traefik using Let's Encrypt. Let me know if you want guidance on that!
