FROM php:5.6-apache
COPY ./my-httpd.conf /etc/apache2/sites-available/000-default.conf
COPY ./my-ssl.conf /etc/apache2/sites-available/default-ssl.conf

# PHP INSTALL
RUN apt-get update \
  && apt-get install -y \
    vim \
    git \
    wget \
    unzip \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng12-dev \
    openssl libssl-dev \
    libxml2-dev \
    && docker-php-ext-install -j$(nproc) iconv mcrypt pdo_mysql mysqli mysql mbstring json xml tokenizer zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini

# PECL extensions
RUN pecl install APCu-4.0.10 redis \
    && docker-php-ext-enable apcu redis

# apache rewrite enable.
RUN cd /etc/apache2/mods-enabled \
    && ln -s ../mods-available/rewrite.load

# composer install
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer

COPY php.ini /usr/local/etc/php/

