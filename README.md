docker-h2
=========

Dockerized H2 database service.


## Features

* Based on [the `OpenJDK` official image](https://hub.docker.com/r/_/openjdk/)
* H2-DATA location on `/opt/h2-data`
* A mix of [zhilvis/docker-h2](https://github.com/zhilvis/docker-h2) and [zilvinasu/h2-dockerfile](https://github.com/zilvinasu/h2-dockerfile).
* This work: https://github.com/oscarfonts/docker-h2


## Trusted builds

[Automated builds](https://hub.docker.com/r/gurghet/h2/) on [docker registry](https://registry.hub.docker.com/):

* [`latest`, `1.0.0` (*1.0.0/Dockerfile*)](https://github.com/gurghet/docker-h2/blob/master/1.0.0/Dockerfile)


## Running

Get the image:

```
docker pull gurghet/h2
```

Run as a service, exposing ports 1521 (TCP database server) and 81 (web interface) and mapping DATA_DIR to host:

```
export WEB_PORT=81
export TCP_PORT=1521
docker run -d -p 1521:1521 -p 81:81 -v /path/to/local/data_dir:/opt/h2-data -e WEB_PORT -e TCP_PORT --name=MyH2Instance gurghet/h2
```

The H2 web console will be available at: http://localhost:81

See the logs while running:

```
docker logs -f MyH2Instance
```
