FROM php:8-fpm
ARG PHP_INI_DIR=/usr/local/etc/php
ARG PGID=1000
ARG PUID=1000
ENV PUID ${PUID}
ENV PGID ${PGID}

COPY ./php.ini ${PHP_INI_DIR}/conf.d/docker-php-config.ini

RUN apt update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev gnupg procps openssl unzip zlib1g-dev libzip-dev libfreetype6-dev libpng-dev libjpeg-dev libicu-dev libonig-dev libxslt1-dev acl nano\
    && docker-php-ext-install intl opcache pdo pdo_mysql \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip

RUN pecl install xdebug


RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony

RUN groupadd -g ${PGID} user 
RUN useradd -l -u ${PUID} -g user -m user

USER user

WORKDIR /var/www/project
