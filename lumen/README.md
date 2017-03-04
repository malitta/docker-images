# Docker Lumen Base Image

Lightweight image containing the bare necessities for running a [Lumen](https://lumen.laravel.com) app over HTTP/HTTPS. This is intended to be used as a base image for your app specific Dockerfiles. [Read this](https://github.com/malitta/docker-images/kb/extending-image.md) for a quick introduction on how this image can be extended to suit your app. 

[![Docker Automated buil](https://img.shields.io/docker/automated/malitta/lumen.svg)](https://hub.docker.com/u/malitta/lumen)
[![Docker Pulls](https://img.shields.io/docker/pulls/malitta/lumen.svg)](https://hub.docker.com/r/malitta/lumen)

## Contains

This is an extension of [malitta/php-base](https://hub.docker.com/r/malitta/php-base). In addition, this image contains:

- PHP extensions
	- mcrypt
	- mbstring

## Usage

#### Extending the Dockerfile

Create a `Dockerfile` and add other dependencies that your app requires. [See here]() for addons that you can use if you are planning to have a seperate Dockerfile for development.

```
FROM malitta/lumen

RUN apt-get install -y php7.0-pgsql	

COPY . /var/www/
```

#### Running a container

Run the following command from the root of your application directory 

`docker run -dit -p 8080:80 -v $(pwd):/var/www --name mywebapp malitta/lumen`

Visit `localhost:8080` from the browser and you should see your application.