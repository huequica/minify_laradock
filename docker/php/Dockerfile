FROM php:7.3-fpm

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Composer install
COPY ./docker/php/php.ini /usr/local/etc/php

RUN apt-get update \
  && apt-get install -y libzip-dev mariadb-client \
  && docker-php-ext-install zip pdo_mysql

ENV COMPOSER_ALLOW_SUPERUSER 1

WORKDIR /var/www