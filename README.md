# Dockerized Clair

This image makes [Clair](https://github.com/coreos/clair) a Vulnerability Static Analysis for Containers usable in Dockerized environments. In accordance with the [12 Factor manifesto](https://12factor.net/),
Apps should be configurable via environment variables. This is not possible with plain Clair out of the box. This repository changes it. Now you don't need to mount Clair config file into the Container.

## Details

This Image extends the [official Clair](https://quay.io/repository/coreos/clair) Image and uses [dockerize](https://github.com/jwilder/dockerize).

## Usage

This image is pushed to [hub.docker.com](https://hub.docker.com/r/8gears/dockerized-clair/) and [docker.8gears.com](https://docker.8gears.com).
```sh
docker pull 8gears/dockerized-clair:stable
```

```
docker pull docker pull docker.8gears.com/dockerized-clair:stable
```

### Run

```sh
docker run -ti \
    -e DB_HOST \
    -e DB_USER \
    -e DB_PASSWORD \
    8gears/dockerized-clair:stable
````
Or use the Docker-Compose file.

### Versions

- **latest**: Represents the latest version that was build. For testing.
- **stable**: Represents the latest stable version. Latest stable version.
- **v2.x.y**: Tagged with the same version as Clair. Latest tagged versions have a also a *stable* sibling.

## Variables

This environment variables can be set to configure Clair.

- DB_HOST _default: postgresdb
- DB_PORT _default: 5432_
- DB_USER _default: clair_
- DB_PASSWORD _default: _
- DB_SSLMODE _default: disable_
- DB_STATEMENT_TIMEOUT _default: 60000_

Should you need additional variables from clair, open an issue or better make a PR with updated [config.tpl.yaml](/config.tpl.yaml) file.

## Docker Compose

This project comes with a ready to use Docker Compose File. You can either download the docker-compose.yml file and modify it or create a .env file and run the following command.

```sh
docker-compose -f https://raw.githubusercontent.com/8gears/dockerized-clair/master/docker-compose.yml up -d -e DB_PASSWORD=bigsecret
```
