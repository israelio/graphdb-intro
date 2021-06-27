# Graph Notebook Docker Image

Dockerfile based on https://github.com/aws/graph-notebook

Docker image is available in https://hub.docker.com/repository/docker/israelio/graphdb-intro

`docker pull israelio/graphdb-intro:latest`

### Using docker-compose
Initially, graph-notebook docker image comes with `GeekTime - Intro to Gremlin and Graph databases.ipynb` starter notebook that comes with a working example of connecting to gremlin and executing a simple gremlin command.

In order to add custom notebooks, you may use the volumes and override/add to `/root/notebook/`.
```
version: '3.4'

services:
  gremlin:
      image: barrman/gremlin-server
      ports:
        - '8182:8182'

  graph-notebook:
    image: israelio/graphdb-intro:latest
    ports:
      - "8888:8888"
    depends_on:
      - gremlin
```
