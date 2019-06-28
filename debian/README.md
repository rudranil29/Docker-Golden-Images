# NGINX golden image

The image uses debian:jessie-slim from docker hub as default source which can be overriden via a runtime argument.

## Build
```
docker build -t debian-base --build-arg DEBIAN_IMAGE=debian:jessie-slim
```
If you don't specify --build-arg, then Docker will use the default value in the ARG.


