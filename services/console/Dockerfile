FROM php:7.0
MAINTAINER wanghao <wanghao@ninghao.net>

WORKDIR /mnt/app

# 常用工具
# glibc-common，重新安装一下支持的语言，因为我需要简体中文
RUN apt-get update && apt-get install -y git curl wget cron vim libfreetype6-dev mariadb-client \
  && rm -rf /var/lib/apt/lists/* \
  && yum reinstall glibc-common -y \
  && pecl install zip \
  && docker-php-ext-enable zip \
  && docker-php-ext-install mysqli pdo_mysql

# 把语言设置成简体中文
ENV LANG zh_CN.UTF-8
ENV LC_ALL=zh_CN.UTF-8
ENV LANGUAGE zh_CN:zh

# 配置 git
RUN git config --global user.name "wanghao8080" \
  && git config --global user.email "117663444@qq.com"

# 安装与配置 composer
# Composer 官方安装脚本 https://getcomposer.org/download/
# 因为在国内下载 composer 太慢，我们直接把下载下来的 composer 复制到容器里使用。
COPY ./composer-1.1.3.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer
RUN echo 'export PATH="$PATH:$HOME/.composer/vendor/bin"' >> ~/.bashrc \
  && . ~/.bashrc \
  && composer config -g repo.packagist composer https://packagist.phpcomposer.com

# 安装管理 WordPress 项目的 wp-cli
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
  && chmod +x wp-cli.phar \
  && mv wp-cli.phar /usr/local/bin/wp

# 安装管理 Drupal 项目的 drush
RUN php -r "readfile('http://files.drush.org/drush.phar');" > drush \
  && chmod +x drush \
  && mv drush /usr/local/bin
