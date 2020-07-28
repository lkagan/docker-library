FROM php:7.4-fpm-alpine
RUN  apk add --update \
        autoconf \
        build-base \
        msmtp \
        libjpeg-turbo-dev \
        libpng-dev \
        libzip \
        libzip-dev \
        composer \
    && pecl install redis-3.1.6 \
    && pecl install zip \
    && pecl install xdebug-2.8.1 \
    && docker-php-ext-enable redis xdebug 
RUN docker-php-ext-configure gd -with-jpeg=/usr/include/ \
    && docker-php-ext-install bcmath exif gd mysqli pdo pdo_mysql opcache 
