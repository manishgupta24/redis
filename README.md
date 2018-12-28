## Redis Dockerfile


This repository contains **Dockerfile** of [Redis](http://redis.io/) for [Docker](https://www.docker.com/)'s published to the public [Docker Hub](https://hub.docker.com/r/manish24/redis).



### Base Docker Image

* [ubuntu:bionic](https://hub.docker.com/_/ubuntu)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Pull image from docker repository: `docker pull manish24/redis`

   (alternatively, you can build an image from Dockerfile: `docker build -t="manish24/redis" https://github.com/manishgupta24/redis/blob/master/Dockerfile`)


### Usage

#### Run `redis-server`

    docker run -d --name redis -p 6379:6379 manish24/redis

#### Run `redis-server` with persistent data directory. (creates `dump.rdb`)

    docker run -d -p 6379:6379 -v <data-dir>:/data --name redis manish24/redis

#### Run `redis-server` with persistent data directory and password. Default Password is redis12345.

    docker run -d -p 6379:6379 -v <data-dir>:/data --name redis manish24/redis redis-server /etc/redis/redis.conf --requirepass <password>

#### Run `redis-cli`

    docker run -it --rm --link redis:redis manish24/redis bash -c 'redis-cli -h redis'
