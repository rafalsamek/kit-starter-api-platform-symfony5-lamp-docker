FROM php:7.4.0-apache

# apt-get update and install required Ubuntu packages
RUN apt-get update \
 && apt-get install -y curl git zlib1g-dev default-mysql-client libzip-dev unzip

 # install required php extensions
RUN docker-php-ext-install zip pdo pdo_mysql mysqli

 # install and configure xdebug
RUN pecl install xdebug \
 && docker-php-ext-enable xdebug \
 && echo 'zend_extension="/usr/local/lib/php/extensions/no-debug-non-zts-20180731/xdebug.so"' >> /usr/local/etc/php/conf.d/xdebug.ini \
 && echo 'xdebug.remote_enable=1' >> /usr/local/etc/php/conf.d/xdebug.ini \
 && echo 'xdebug.idekey=PHPSTORM' \
 # set autostart to 1, so API calls auto trigger debugger
 && echo 'xdebug.remote_autostart=0' >> /usr/local/etc/php/conf.d/xdebug.ini \
 && echo 'xdebug.remote_connect_back=1' >> /usr/local/etc/php/conf.d/xdebug.ini \
 && echo 'xdebug.remote_port=9000' >> /usr/local/etc/php/conf.d/xdebug.ini

 # enable required apache modules
RUN a2enmod rewrite headers

 # install and configure composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html
