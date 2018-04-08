# JanusGraph Docker container

## About

This project is to deploy [JanusGraph](http://janusgraph.org/), and [Cassandra](http://cassandra.apache.org/) as its database backend, and [ElasticSearch](https://www.elastic.co/products/elasticsearch) as its index backend.

Most of work in this project is done in [this repository](https://github.com/sunsided/janusgraph-docker), with some modifications:

1. Database backend is Cassandra, instead of Scylla.
2. ElasticSearch version is 6.x, which is taken from ElasticSearch's private Docker hub.
3. In `janusgraph/run.sh`, besides ElasticSearch and Cassandra, it also wait for Cassandra Thrift (port `9160`).

## How to run
```
docker-compose up --build
```

Note that a version of [Docker Compose](https://github.com/docker/compose) with support for version `3` schemas is required, e.g. `1.15.0`.

Afterwards, you can connect to the local Gremlin shell using

```
docker exec -it janusgraphdocker_janus_1 ./bin/gremlin.sh
```