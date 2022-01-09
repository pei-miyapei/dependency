FROM php:8.1.0-fpm
COPY php.ini /usr/local/etc/php/

RUN apt-get update \
    && apt-get install -y zlib1g-dev git libzip-dev \
    && docker-php-ext-install zip bcmath

# composer install
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin
RUN composer self-update

ENV LANG=C.UTF-8
ENV LANGUAGE=en_US
WORKDIR /var/www
