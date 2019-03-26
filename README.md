# mongo-seed

> A Docker image to seed your Mongo database.

[![](https://images.microbadger.com/badges/image/stefanwalther/mongo-seed.svg)](https://microbadger.com/images/stefanwalther/mongo-seed "Get your own image badge on microbadger.com")

---

## Purpose

Docker image to seed your mongo database with ease. Available on [Docker Hub](https://hub.docker.com/r/stefanwalther/mongo-seed)

## Installation

```
$ docker pull stefanwalther/mongo-seed[:<version>]
```

## Usage

```yaml
version: '3.3'

services:

  mongo:
    image: mongo
    container_name: mongo
    ports:
      - 27017:27017

  mongo-seed:
    image: stefanwalther/mongo-seed
    container_name: mongo-seed
    environment:
      - MONGODB_HOST=mongo
      - MONGODB_PORT=27017
    volumes:
      - ./config/db-seed:/data
    depends_on:
      - mongo
    command: [
      "mongoimport --host mongo --port 27017 --db sammlerio --mode upsert --type json --file /data/auth-service~~user.json --jsonArray"
    ]

```

## About

### Author
**Stefan Walther**

* [twitter/waltherstefan](http://twitter.com/waltherstefan)
* [github.com/stefanwalther](http://github.com/stefanwalther)
* [LinkedIn](https://www.linkedin.com/in/stefanwalther/) 
* [stefanwalther.io](http://stefanwalther.io) - Private blog

### Contributing
Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/stefanwalther/mongo-seed/issues). The process for contributing is outlined below:

1. Create a fork of the project
2. Work on whatever bug or feature you wish
3. Create a pull request (PR)

I cannot guarantee that I will merge all PRs but I will evaluate them all.

### License
MIT

***

_This file was generated by [verb-generate-readme](https://github.com/verbose/verb-generate-readme), v0.6.0, on March 26, 2019._

