FROM php:7.0
MAINTAINER wanghao <wanghao@ninghao.net>

# 常用工具
RUN apt-get update && apt-get install -y git curl libfreetype6-dev \
  && rm -rf /var/lib/apt/lists/* \
  && pecl install zip \
  && docker-php-ext-enable zip

# 配置 git
RUN git config --global user.name "wanghao8080" \
  && git config --global user.email "117663444@qq.com"

# 安装与配置 composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php -r "if (hash_file('SHA384', 'composer-setup.php') === 'e115a8dc7871f15d853148a7fbac7da27d6c0030b848d9b3dc09e2a0388afed865e6a3d6b3c0fad45c48e2b5fc1196ae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
  && php composer-setup.php \
  && php -r "unlink('composer-setup.php');" \
  && mv composer.phar /usr/local/bin/composer \
  && echo 'export PATH="$PATH:$HOME/.composer/vendor/bin"' >> ~/.bashrc \
  && . ~/.bashrc \
  && composer config -g repo.packagist composer https://packagist.phpcomposer.com

# 安装管理 WordPress 项目的 wp-cli
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
  && chmod +x wp-cli.phar \
  && mv wp-cli.phar /usr/local/bin/wp
