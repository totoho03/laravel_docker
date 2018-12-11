FROM php:7.2.12-fpm-alpine3.8
# 作成したユーザの情報
MAINTAINER honda <toru.pyon@gmail.com>

RUN apk update \
    && apk --no-cache add zlib-dev \
    && apk --no-cache add postgresql-dev \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo_pgsql \
    && docker-php-ext-install mbstring

# install xdebug
RUN apk add --no-cache --virtual buildDeps autoconf build-base\
    && pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && apk del buildDeps build-base


RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php composer-setup.php \
  && php -r "unlink('composer-setup.php');" \
  && mv composer.phar /usr/local/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

RUN composer global require "laravel/installer"

