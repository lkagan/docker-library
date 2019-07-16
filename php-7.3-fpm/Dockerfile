FROM php:7.3-fpm-alpine
RUN  apk add --update \
        autoconf \
        build-base \
        msmtp \
        libjpeg-turbo-dev \
        libpng-dev \
        libzip \
        libzip-dev \
    && docker-php-ext-install mysqli pdo_mysql pdo opcache \
    && docker-php-ext-configure gd --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && pecl install redis-3.1.6 \
    && pecl install xdebug-2.7.2 \
    && pecl install zip
