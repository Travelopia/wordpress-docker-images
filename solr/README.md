# Solr for Pantheon

![maintenance-status](https://img.shields.io/badge/maintenance-actively--developed-brightgreen.svg)

**Docker Hub**: https://hub.docker.com/r/travelopia/solr

Solr Docker image for https://wordpress.org/plugins/solr-power/. Pantheon (unfortunately) currently only supports Solr 3.6:

https://github.com/pantheon-systems/solr-power

> Because Solr Power is intended to be a bridge between WordPress and the Apache Solr search engine, you'll need access to a functioning Solr 3.6 instance for the plugin to work as expected. This plugin does not support other versions of Solr

There are no [official](https://hub.docker.com/_/solr) images for Solr for version 3.6 which support Apple silicon.

This image can be used to build a multi-architecture Solr `3.6.2` version.

## Build Instructions

#### Note: These instructions are for macOS running on an ARM processor.

1. `cd` into the directory with the Dockerfile
2. Create a `buildx` builder, if you don't already have one: `docker buildx create --use --platform=linux/arm64,linux/amd64 --name multi-platform-builder`
   1. This will create a container with prefix `buildx_` - you can delete it once you are done
3. Log in via Docker Desktop, and then run: `docker login`
4. Build and push the image: `docker buildx build --platform linux/amd64,linux/arm64 -t travelopia/solr:3.6.2 --push .`
   1. This may take a long time!
