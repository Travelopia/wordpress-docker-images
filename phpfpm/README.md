# PHP-FPM Images

![maintenance-status](https://img.shields.io/badge/maintenance-actively--developed-brightgreen.svg)

**Docker Hub**: https://hub.docker.com/r/travelopia/wordpress-php-fpm

These images are built to be used with a `docker-compose.yml` file, and contain the following:

1. PHP-FPM
2. Redis
3. WP CLI
4. Composer
5. MailHog

## Build Instructions

#### Note: These instructions are for macOS running on an ARM processor.

1. `cd` into the directory with the Dockerfile
2. Create a `buildx` builder, if you don't already have one: `docker buildx create --use --platform=linux/arm64,linux/amd64 --name multi-platform-builder`
    1. This will create a container with prefix `buildx_` - you can delete it once you are done
3. Build the image: `docker buildx build --platform linux/amd64,linux/arm64 -t wordpress-php-fpm .`
    1. This will load it into memory, but not tag it yet
4. Tag the image: `docker buildx build --load -t wordpress-php-fpm .`
5. Log in via Docker Desktop, and then run: `docker login`
6. Change the image tag locally, for example: `docker tag wordpress-php-fpm travelopia/wordpress-php-fpm:8.1`
7. Push this newly tagged image to Docker Hub: `docker push travelopia/wordpress-php-fpm:8.1`
