# Docker Images

This is a collection of docker images that you can use to easily setup your dev/production environments. All images are auto-built and are available through the Docker Hub under the username [malitta](https://hub.docker.com/u/malitta)

The intension was to build the images as lightweigh as possible to run a certain application, which can then be extended to contain additional requirements needed for that specific project. For example, non of these images include drivers for linking to the persistance layer, because the choice can defer between each project and having all the drivers included in the image for _convenience_ would increase the size of the image unnecessarily.

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

## Usage 

Without using these images to run a container directly, it is highly recommended to create your app specific `Dockerfile` first by extending one of these images. This will give you the flexibility to add additional requirements needed for your project. 

You can easily use one of these images as the example illustrates below.

##### Eg: Starting a new Lumen application using POSTGRESQL for storage

Create a Dockerfile in your project directory.
```
FROM malitta/laravel:5.4

RUN apt-get install -y php7.0-pgsql
```

Build the image by running

`docker build -t phpbase .`

Start a container using the image

`docker run -dit -p 8080:80 -v ./:/var/www laravelapp`

It's as simple as that!  🙌