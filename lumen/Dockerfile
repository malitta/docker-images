FROM malitta/php-base:7.2
MAINTAINER Malitta Nanayakkara <malitta@gmail.com>

RUN apt-get update && apt-get install -y \
	php-mcrypt \	
	php-mbstring

RUN	phpenmod mbstring