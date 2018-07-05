FROM php:7.2.7-cli-alpine
RUN  apk add --update \
        autoconf \
        build-base \
        automake \
        git \
        redis \
        mysql-client \
        openssh-client \
        clang \
        linux-headers \
        python \
        rsync \
    && docker-php-ext-install mysqli pdo_mysql pdo \
    && pecl install redis-3.1.6 \
    && pecl install xdebug-2.6.0 
ADD https://getcomposer.org/download/1.6.3/composer.phar /usr/local/bin/composer
ADD https://phar.phpunit.de/phpunit-7.phar /usr/local/bin/phpunit
RUN cd /usr/local \
    && chmod +x /usr/local/bin/composer /usr/local/bin/phpunit \
    && sed -i 's/PAGER=less/PAGER=more/' /etc/profile \
    && composer global require "squizlabs/php_codesniffer=*" \
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
