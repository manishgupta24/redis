## Redis Dockerfile


This repository contains **Dockerfile** of [Redis](http://redis.io/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/dockerfile/redis/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).


### Base Docker Image

* [ubuntu:bionic](http://dockerfile.github.io/#/ubuntu)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/dockerfile/redis/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull dockerfile/redis`

   (alternatively, you can build an image from Dockerfile: `docker build -t="dockerfile/redis" github.com/dockerfile/redis`)


### Usage

#### Run `redis-server`

    docker run -d --name redis -p 6379:6379 manish24/redis

#### Run `redis-server` with persistent data directory. (creates `dump.rdb`)

    docker run -d -p 6379:6379 -v <data-dir>:/data --name redis manish24/redis

#### Run `redis-server` with persistent data directory and password. Default Password is redis12345.

    docker run -d -p 6379:6379 -v <data-dir>:/data --name redis manish24/redis redis-server /etc/redis/redis.conf --requirepass <password>

#### Run `redis-cli`

    docker run -it --rm --link redis:redis dockerfile/redis bash -c 'redis-cli -h redis'
