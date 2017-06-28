FROM php:7.0-fpm

RUN apt-get update && apt-get install -y \
        libcurl4-gnutls-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        libxml2-dev \
        libxslt-dev \
        libzzip-dev \
    && docker-php-ext-install -j$(nproc) curl iconv json mbstring mcrypt mysqli pdo_mysql soap sockets xml xsl zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd


# libxml2-dev libbz2-dev libpng++-dev libjpeg-dev zlib1g-dev libgd-dev
