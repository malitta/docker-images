# Docker PHP Base Image

Lightweight image containing the bare necessities for running a PHP app over HTTP/HTTPS. This is intended to be used as a base image for your app specific Dockerfiles. See docker-images repository for extensions of this image. 

## Contains

- Ubuntu ([latest LTS](https://wiki.ubuntu.com/LTS))
- PHP 7.0
- Apache 2.4 (HTTP/1.1)

## Usage

#### Extending the Dockerfile

Create a `Dockerfile` and add other dependencies that your app requires. [See here](/) for addons that you can use if you are planning to have a seperate Dockerfile for development.

```
FROM malitta:php-base

RUN apt-get install -y php7.0-pgsql	

COPY . /var/www/html
```

#### Running a container

`docker run -dit -p 8080:80 -v :/var/www/html --name mywebapp malitta/php-base`

Visit `localhost:8080` from the browser and you should see the _PHP Version Info_ page.