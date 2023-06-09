# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.241.1/containers/rust/.devcontainer/base.Dockerfile

# [Choice] Debian OS version: buster, bullseye, bookworm
ARG VARIANT="bullseye"

# Which OS shall we run as the base?
FROM mcr.microsoft.com/vscode/devcontainers/rust:0-${VARIANT}

COPY ./packages.txt ./packages.txt

#VOLUME "/var/run/docker.sock:/var/run/docker.sock:ro"

# ENV key1=value1
# or use docker-compose.yaml to load from a file

RUN export DEBIAN_FRONTEND=noninteractive \
    && apt-get update \
    && apt-get upgrade -y \
    && xargs -a ./packages.txt apt-get install -y

# install django and gunicorn for Python UIs
COPY ./requirements.txt ./requirements.txt

RUN pip install -r requirements.txt

ENTRYPOINT /bin/bash
