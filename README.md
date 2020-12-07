# training-day

A very NOT-FOR-PROD Docker in Docker Container that runs a Nomad Client. This should not be used anywhere near a production/real use case. Again, you definitely shouldn't.

## Running stack in Docker

The Dockerfile builds a Ubuntu 18.04 image using the build scripts in this directory.

### Quickstart

The following creates a fresh terminal session using the image:

```shell
make && docker exec -it hashistack bash
```

> The container is reset each time the make command is run.

## Manual instructions

Use these steps if you prefer to change or update the docker flags.

Built the docker container

```shell
docker build \
         --rm \
         -t \
         hashistack:latest
```

### Run hashistack container

Launch the hashistack container in the background.

```shell
docker run \
  -d \
  -v /var/run/docker.sock:/var/run/docker.sock \
  --name \
  hashistack \
  hashistack
```

> The -v flag is optional but allows docker (in docker) to use the hosts docker api.

## Exec to the running container

Connect to the hashistack container for interactive testing.

```shell
docker exec -it hashistack bash
```

## Resetting the container

View the running containers

```shell
docker ps
CONTAINER ID        IMAGE               COMMAND               CREATED             STATUS              PORTS               NAMES
08a114d9aa4d        5fdc74d879ca        "tail -f /dev/null"   3 minutes ago       Up 3 minutes                            hashistack
```

Remove the running container

```shell
docker rm -f hashistack
```

> **All session state is destroyed.**
