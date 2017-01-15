FROM ubuntu:16.04

MAINTAINER James Ward <james@notjam.es>

ENV HOME "/root"
ENV PATH "~/.yarn/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
ENV COMPOSER_HOME /root/composer

ENV DEBIAN_FRONTEND=noninteractive

ENV LANG       en_US.UTF-8
ENV LC_ALL en_US.UTF-8

RUN locale-gen en_US.UTF-8

# Update the installation
RUN apt-get update
RUN apt-get upgrade -y

# PHP Installation
RUN apt-get remove -y --purge php5 php5-common

RUN apt-get install -y \
		php7.0-common \
		php7.0-cli \
		php7.0-fpm \
		php7.0-dev \
		php7.0-opcache \
		php7.0-pgsql \
		php7.0-readline \
		php7.0-mcrypt \
		php7.0-zip \
		php7.0-xml \
		php7.0-mbstring \
		php7.0-curl \
		php7.0-json \
		php7.0-sqlite3 \
		php7.0-tokenizer \
		php7.0-imap \
		php-msgpack \
		php7.0-gd

# Install composer
VOLUME /root/composer

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer selfupdate
RUN composer global require hirak/prestissimo --prefer-dist --no-interaction

# NodeJS installation
RUN curl -sL https://deb.nodesource.com/setup_7.x | bash -
RUN apt-get install -y nodejs

RUN npm install -g gulp
RUN npm install -g grunt

# YARN
RUN curl -o- -L https://yarnpkg.com/install.sh | bash
