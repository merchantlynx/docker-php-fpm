FROM composer:latest as composer

FROM php:7.1-fpm-alpine
COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN docker-php-ext-install bcmath
RUN apk add imap-dev
RUN docker-php-ext-install imap
RUN docker-php-ext-install pcntl
RUN docker-php-ext-install pdo_mysql
#RUN docker-php-ext-install pdo_pgsql
#RUN docker-php-ext-install pdo_sqlite
RUN apk add libxml2-dev
RUN docker-php-ext-install xml
RUN apk add libzip-dev
RUN docker-php-ext-install zip
