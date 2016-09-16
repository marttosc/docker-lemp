FROM ubuntu:16.04

MAINTAINER Gustavo Marttos <marttosc@gmail.com>

RUN DEBIAN_FRONTEND=noninteractive

RUN locale-gen pt_BR.UTF-8

ENV LANGUAGE=pt_BR.UTF-8
ENV LC_ALL=pt_BR.UTF-8
ENV LC_CTYPE=UTF-8
ENV LANG=pt_BR.UTF-8
ENV TERM xterm

RUN apt-get update && \
	apt-get install -y software-properties-common && \
	apt-get install -y --force-yes \
		php7.0-cli \
	        php7.0-common \
	        php7.0-curl \
	        php7.0-json \
	        php7.0-xml \
	        php7.0-mbstring \
	        php7.0-mcrypt \
	        php7.0-mysql \
	        php7.0-sqlite \
	        php7.0-sqlite3 \
	        php7.0-zip \
	        php7.0-gd \
	        pkg-config \
	        php-dev \
        	libcurl4-openssl-dev \
	        libedit-dev \
	        libssl-dev \
	        libxml2-dev \
        	xz-utils \
		libsqlite3-dev \
	        sqlite3 \
        	git \
		curl \
        	vim \
	        nano \
	&& apt-get clean

RUN curl -s http://getcomposer.org/installer | php && \
	echo "export PATH=${PATH}:/var/www/laravel/vendor/bin" >> ~/.bashrc && \
	mv composer.phar /usr/local/bin/composer

RUN . ~/.bashrc

ARG PUID=1000
ARG PGID=1000

RUN groupadd -g $PGID lemp_user && \
    useradd -u $PUID -g lemp_user -m lemp_user

RUN chown -R lemp_user:lemp_user /home/lemp_user/

USER lemp_user

USER root
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /var/www/app

