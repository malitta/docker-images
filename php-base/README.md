# Docker PHP Base Image

Lightweight image containing the bare necessities for running a PHP app over HTTP/HTTPS. This is intended to be used as a base image for your app specific Dockerfiles. See [docker-images](https://github.com/malitta/docker-images) repository for extensions of this image. Or [read this](https://github.com/malitta/docker-images/kb/extending-image.md) for a quick introduction on how this image can be extended to suit your app. 

[![Docker Automated buil](https://img.shields.io/docker/automated/malitta/php-base.svg)](https://hub.docker.com/u/malitta/php-base)
[![Docker Pulls](https://img.shields.io/docker/pulls/malitta/php-base.svg)](https://hub.docker.com/r/malitta/php-base)

## Contains

- Ubuntu ([latest LTS](https://wiki.ubuntu.com/LTS))
	- Supervisor
	- Vim
- PHP 7.3
	- Composer
- Apache 2.4 (HTTP/1.1)

## Usage

Note: The default virtualhost file points to `/var/www/public`

#### Extending the Dockerfile

Create a `Dockerfile` and add other dependencies that your app requires. [See here](/) for addons that you can use if you are planning to have a seperate Dockerfile for development.

```
FROM malitta/php-base

RUN apt-get install -y php7.3-pgsql	

COPY . /var/www
```

#### Running a container

`docker run -dit -p 8080:80 -v $(pwd):/var/www --name mywebapp malitta/php-base`

Visit `localhost:8080` from the browser and you should see the _PHP Version Info_ page.