FROM composer:latest as composer

FROM php:7.1-fpm-alpine
COPY --from=composer /usr/bin/composer /usr/bin/composer

ENV PHP_MAX_EXECUTION_TIME="30" \
    PHP_POST_MAX_SIZE="8M" \
    PHP_UPLOAD_MAX_FILESIZE="2M" \
    PHP_DATE_TIMEZONE="America/New_York" \
    PHP_OPCACHE_VALIDATE_TIMESTAMPS="0" \
    PHP_OPCACHE_MAX_ACCELERATED_FILES="10000" \
    PHP_OPCACHE_MEMORY_CONSUMPTION="192" \
    PHP_OPCACHE_MAX_WASTED_PERCENTAGE="10"

COPY php.ini /usr/local/etc/php/php.ini

RUN docker-php-ext-install bcmath
RUN apk add imap-dev
RUN docker-php-ext-install imap
RUN docker-php-ext-install opcache
COPY opcache.ini /usr/local/etc/php/conf.d/opcache.ini
RUN docker-php-ext-install pcntl
RUN docker-php-ext-install pdo_mysql
#RUN docker-php-ext-install pdo_pgsql
#RUN docker-php-ext-install pdo_sqlite
RUN apk add libxml2-dev
RUN docker-php-ext-install xml
RUN apk add libzip-dev
RUN docker-php-ext-install zip
RUN apk add gnupg
