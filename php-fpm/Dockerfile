FROM php:7.0-fpm

MAINTAINER Gustavo Marttos <marttosc@gmail.com>

RUN apt-get update && \
	apt-get install -y --no-install-recommends \
	curl \
	libz-dev \
	libpq-dev \
	libjpeg-dev \
	libpng12-dev \
	libfreetype6-dev \
	libssl-dev \
	libmcrypt-dev

RUN docker-php-ext-install mcrypt

RUN docker-php-ext-install pdo_mysql

RUN docker-php-ext-install xml

ADD ./custom.ini /usr/local/etc/php/conf.d
ADD ./custom.pool.conf /usr/local/etc/php-fpm.d/

RUN rm -r /var/lib/apt/lists/*

RUN usermod -u 1000 www-data

WORKDIR /var/www/app

CMD ["php-fpm"]

EXPOSE 9000

