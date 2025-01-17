[![build our image](https://github.com/langerma/docker-glibc-builder/actions/workflows/image.yml/badge.svg)](https://github.com/langerma/docker-glibc-builder/actions/workflows/image.yml)

# docker-glibc-builder

A glibc binary package builder in Docker. Produces a glibc binary package that can be imported into a rootfs to run applications dynamically linked against glibc.

## Usage

Build a glibc package based on version 2.34 with a prefix of `/usr/glibc-compat`:

    docker run --rm --env STDOUT=1 langerma/glibc-builder 2.34 /usr/glibc-compat > glibc-bin-2.34-aarch64.tar.gz

You can also keep the container around and copy out the resulting file:

    docker run --name glibc-binary langerma/glibc-builder 2.34 /usr/glibc-compat
    docker cp glibc-binary:/glibc-bin-2.34.tar.gz ./
    docker rm glibc-binary
