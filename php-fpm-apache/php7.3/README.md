# Docker Stack for Apache2.4 and php7.3 environment

## Summary

A simple Dockerfile for apache 2.4 and php-fpm 7.3

- Based on debian
- With apache 2.4 + php7.3-fpm
- Custom apache 2.4, php7.3 and supervisord configurations

## Usage

### Development

```
docker build -t apache-php7.3-fpm-base --build-arg DEBIAN_IMAGE=quay.io/srijan/debian .;
docker run apache-php7.3-fpm -p 80:80;
```

### Debugging

Login:

```
docker exec -it apache-php7.3-fpm-base /bin/bash
```

### PHP Extension Enabled

```
RUN apt-get update -y && \
    apt-get install -y \
    mysql-client \
    php7.3-dev \
    php7.3  \
    php7.3-cli \
    php7.3-fpm \
    php7.3-common \
    php7.3-curl \
    php7.3-gd \
    php7.3-memcached \
    php7.3-xdebug \
    php-pear \
    php7.3-json \
    php7.3-mbstring \
    php7.3-intl \
    php7.3-mysql \
    php7.3-xml \
    php7.3-zip \
    php7.3-apcu \
    php7.3-ctype \
    php7.3-dom \
    php7.3-iconv \
    php7.3-imagick \
    php7.3-json \
    php7.3-intl \
    php7.3-opcache \
    php7.3-pdo \
    php7.3-mysqli \
    php7.3-xml  \
    php7.3-tokenizer \
    php7.3-zip \
    php7.3-simplexml \
    php7.3-bcmath \
    libapache2-mod-php7.3 \
```

### PHP Dependency management tool

```
RUN curl -sS https://getcomposer.org/installer | php \
   && mv composer.phar /usr/local/bin/composer
```