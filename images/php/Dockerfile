FROM php:7.0-fpm
MAINTAINER wanghao <wanghao@ninghao.net>

RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev \
  && rm -rf /var/lib/apt/lists/* \
  && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
  && docker-php-ext-install gd

COPY ./config/php.ini /usr/local/etc/php/conf.d/
