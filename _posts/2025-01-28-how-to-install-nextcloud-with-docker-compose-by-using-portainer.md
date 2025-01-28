---
title: NextCloud instalation with Docker
date: 2025-01-28 11:13:05 +/-TTTT
categories: ["Tech", "Solutions"]
tags: ["docker", "linux", "nextcloud"]     # TAG names should always be lowercase
description: Docker Compose code to install nexcloud on docker
---

## Docker Compose code to install nexcloud on docker

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
      - MYSQL_PASSWORD=Mehraj@#2011

  db:
    image: mariadb:latest
    container_name: nextcloud_db
    restart: always
    environment:
      - MYSQL_ROOT_PASSWORD=Mehraj@#2011
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextclouduser
      - MYSQL_PASSWORD=Mehraj@#2011
    volumes:
      - db_data:/var/lib/mysql

volumes:
  nextcloud_data:
  db_data:
```
