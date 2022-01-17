FROM php:fpm-alpine

RUN apk update \
    && apk add --no-cache \
    supervisor \ 
    libxml2-dev \
    openssh \
    php7 \
    nodejs \
    npm \
    gnupg \
    git \
    libzip-dev zip unzip \
    libpq-dev \
    openssl \
    gcc \
    musl-dev \
    make \
    && apk add --no-cache --virtual .build-deps $PHPIZE_DEPS \
    && pecl install xdebug-3.1.2 \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-configure pdo \
    && docker-php-ext-install pdo \
    && docker-php-ext-enable pdo \
    && docker-php-ext-configure pdo_mysql \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-enable pdo_mysql \
    && docker-php-ext-configure pdo_pgsql \
    && docker-php-ext-install pdo_pgsql \
    && docker-php-ext-enable pdo_pgsql \
    && docker-php-ext-configure opcache \
    && docker-php-ext-install opcache \
    && docker-php-ext-enable opcache \
    && npm i -g npm@8.1.2 \
    && npm i -g npx \
    ;

COPY ./supervisord.conf /etc/supervisord.conf

RUN /bin/sh -c set -eux

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"]

EXPOSE 22