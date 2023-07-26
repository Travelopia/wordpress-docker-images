# PHP-FPM Images

![maintenance-status](https://img.shields.io/badge/maintenance-actively--developed-brightgreen.svg)

**Docker Hub**: https://hub.docker.com/r/travelopia/wordpress-php-fpm

These images are built to be used with a `docker-compose.yml` file, and contain the following:

1. PHP-FPM
1. XDebug
1. Redis
1. Composer
1. WP CLI
1. MailHog

## Build Instructions

#### Note: These instructions are for macOS running on an ARM processor.

1. `cd` into the directory with the Dockerfile
2. Create a `buildx` builder, if you don't already have one: `docker buildx create --use --platform=linux/arm64,linux/amd64 --name multi-platform-builder`
   1. This will create a container with prefix `buildx_` - you can delete it once you are done
3. Log in via Docker Desktop, and then run: `docker login`
4. Build and push the image, example: `docker buildx build --platform linux/amd64,linux/arm64 -t travelopia/wordpress-php-fpm:8.1 --push .`
   1. This may take a long time!
