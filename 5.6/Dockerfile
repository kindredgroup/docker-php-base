FROM php:5.6-apache-jessie
MAINTAINER karel.bemelmans@kindredgroup.com

# install the PHP extensions we need
RUN set -x && apt-get update && apt-get install -y \
    libpng12-dev \
    libjpeg-dev \
    libpq-dev \
    mysql-client \
    wget \
  && rm -rf /var/lib/apt/lists/* \
  && pecl install memcache-3.0.8 uploadprogress \
  && docker-php-ext-enable memcache uploadprogress \
  && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
  && docker-php-ext-install gd mbstring opcache pdo pdo_mysql pdo_pgsql sockets zip \
  && rm -rf /var/lib/apt/lists/*

# Install a recent version of jq, Debian has an old version
RUN curl -o /usr/local/bin/jq -Ls https://github.com/stedolan/jq/releases/download/jq-1.5/jq-linux64 \
  && chmod +x /usr/local/bin/jq

