# Docker Stack for Apache2.4 and php7.2 environment

## Summary

A simple Dockerfile for apache 2.4 and php-fpm 7.2

- Based on debian
- With apache 2.4 + php-fpm7.2
- Custom apache 2.4, php7.2 and supervisord configurations

## Usage

### Development

```
docker build -t apache-php7.2-fpm-base --build-arg DEBIAN_IMAGE=debian:jessie-slim .;
docker run apache-php7.2-fpm -p 80:80;
```

### Debugging

Login:

```
docker exec -it apache-php7.2-fpm-base /bin/bash
```

### PHP Extension Enabled

```
RUN apt-get update -y && \
    apt-get install -y \
    mysql-client \
    php7.2-dev \
    php7.2  \
    php7.2-cli \
    php7.2-fpm \
    php7.2-common \
    php7.2-curl \
    php7.2-gd \
    php7.2-memcached \
    php7.2-xdebug \
    php-pear \
    php7.2-json \
    php7.2-mbstring \
    php7.2-intl \
    php7.2-mysql \
    php7.2-xml \
    php7.2-zip \
    php7.2-apcu \
    php7.2-ctype \
    php7.2-dom \
    php7.2-iconv \
    php7.2-imagick \
    php7.2-json \
    php7.2-intl \
    php7.2-opcache \
    php7.2-pdo \
    php7.2-mysqli \
    php7.2-xml  \
    php7.2-tokenizer \
    php7.2-zip \
    php7.2-simplexml \
    php7.2-bcmath \
    libapache2-mod-php7.2 \
```

### PHP Dependency management tool

```
RUN curl -sS https://getcomposer.org/installer | php \
   && mv composer.phar /usr/local/bin/composer
```
