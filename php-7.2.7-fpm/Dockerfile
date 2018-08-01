FROM php:7.2.7-fpm-alpine3.7
RUN  apk add --update \
        autoconf \
        build-base \
        msmtp \
        libjpeg-turbo-dev \
        libpng-dev \
    && docker-php-ext-install mysqli pdo_mysql pdo opcache gd \
    && pecl install redis-3.1.6 \
    && pecl install xdebug-2.6.0
