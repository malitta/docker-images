FROM ubuntu:latest
MAINTAINER Malitta Nanayakkara <malitta@gmail.com>

RUN apt-get update && apt-get install -y \
	apache2 \	
	curl \
	libapache2-mod-php7.0 \
	php7.0 \	
	php-curl \	
	php-xml \	
	vim \
	wget

RUN curl -sS https://getcomposer.org/installer | \
	php -- --install-dir=/usr/local/bin --filename=composer

# Clean up the apt cache
RUN rm -rf /var/lib/apt/lists/*

RUN rm -rf /var/www/html
COPY ./files/public /var/www/public
COPY ./files/000-default.conf /etc/apache2/sites-available/000-default.conf

RUN a2enmod rewrite headers

EXPOSE 80 443

WORKDIR /var/www

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]