FROM php:5.6.40-apache
RUN docker-php-ext-install mysqli mysql pdo_mysql pdo opcache \
    && a2enmod rewrite \
    && apt-get update \
    && apt-get install -y less unzip msmtp \
    && pecl install redis-3.1.6 \
    && pecl install xdebug-2.5.5
