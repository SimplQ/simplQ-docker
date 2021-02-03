# simplQ-docker

> **This is work in progress and not yet ready for usage.**

This is the git repo of the official Docker image for [SimplQ.me](https://simplq.me). 

## Get Started in Two Minutes

To run SimplQ on your machine, [install docker](https://docs.docker.com/get-docker/) and then do:

```
docker run -d --name simplq -p 9000:9000 simplq:latest
```

Once your instance is up and running, SimplQ is ready to be used at http://localhost:9000 

## Configuration

By default, the image will use an embedded H2 database that is not suited for production. Set up a Postgres database and supply the connection URL to the docker image:

```
DB_HOSTNAME=<db-server-url>
DB_PORT=<db-port>
DB_DB_NAME=<db-name>
DB_USERNAME=<db-user>
DB_PASSWORD=<db-password>
```

## TODOs

This is just the initial idea, yet to be implemented. We will need to write a docker image that will run the frontend and backend together, and expose it on a single port [using a nginx reverse proxy](https://www.digitalocean.com/community/tutorials/docker-explained-how-to-containerize-and-use-nginx-as-a-proxy) if possible.

It would require some minor tweaks in the application code, for example the DB connection environment variables currently have the prefix `RDS_` which we would need to rename to `DB_`. Also for frontend, the backend URL and other paramters are currently hardcoded in code. We would need to find a way to configure them at build time or runtime via environment variables. 
