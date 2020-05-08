FROM php:7.4.5-cli-alpine3.11
RUN  apk add --update \
        autoconf \
        build-base \
        automake \
        msmtp \
        git \
        redis \
        mysql-client \
        openssh-client \
        clang \
        linux-headers \
        python \
        rsync \
        libjpeg-turbo-dev \
        libpng-dev \
        libzip \
        libzip-dev 
RUN pecl install redis-3.1.6 \
    && pecl install xdebug-2.8.1 \
    && pecl install zip \
    && pecl install pcov \
    && docker-php-ext-enable pcov
RUN docker-php-ext-configure gd -with-jpeg=/usr/include/ \
    && docker-php-ext-install bcmath exif gd mysqli pdo pdo_mysql opcache pcntl
ADD https://getcomposer.org/download/1.6.3/composer.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer \
    && sed -i 's/PAGER=less/PAGER=more/' /etc/profile \
    && echo 'export PATH=$PATH:/root/.composer/vendor/bin' >> /etc/profile \
    && curl https://nodejs.org/dist/v8.11.2/node-v8.11.2.tar.gz --output /tmp/node.tgz \
    && cd /tmp \
    && tar -xvzf node.tgz \
    && rm node.tgz \
    && cd /tmp/node-v8.11.2 \
    && ./configure \
    && make -j4 \
    && make install
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
    && chmod +x wp-cli.phar \
    && mv wp-cli.phar /usr/local/bin/wp \
    && echo 'alias wp="wp --allow-root"' >> /etc/profile
