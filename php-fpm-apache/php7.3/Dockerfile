ARG DEBIAN_IMAGE=debian:jessie-slim
FROM $DEBIAN_IMAGE

RUN apt-get update \
    && apt-get install --no-install-recommends -y \
    gnupg \
    curl wget vim openssh-server software-properties-common netcat apachetop htop

RUN apt-get install --no-install-recommends -y build-essential apt-transport-https lsb-release ca-certificates -y
RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list

# Install all the PHP dependencies
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
    apache2 \
    libapache2-mod-fcgid \
    rsyslog --force-yes

RUN a2enmod actions && a2enmod proxy && a2enmod rewrite && a2enconf php7.3-fpm && a2enmod proxy_fcgi && rm -rf /var/lib/apt/lists/*

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php \
   && mv composer.phar /usr/local/bin/composer

# PHP Configuration
COPY docker-utils/php/php.ini /etc/php/7.3/fpm/php.ini
COPY docker-utils/php/pool.d/www.conf /etc/php/7.3/fpm/pool.d/www.conf

# Apache configurations
COPY docker-utils/apache2/app.conf /etc/apache2/sites-enabled/000-default.conf
# Disable Xdebug
RUN phpdismod xdebug

COPY docroot /var/www/html
RUN chown www-data:www-data /var/www
EXPOSE 80
CMD service php7.3-fpm start && /usr/sbin/apache2ctl -D FOREGROUND
