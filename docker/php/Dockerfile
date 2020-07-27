FROM php:7.4-fpm
COPY php.ini /usr/local/etc/php/

RUN apt-get update \ 
  && apt-get install -y libzip-dev \
  &&  curl -sL https://deb.nodesource.com/setup_12.x | bash - \
  && apt-get install -y nodejs \
  && pecl install xdebug \
  && docker-php-ext-enable xdebug 

RUN apt-get install -y libpq-dev \
  && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
  && docker-php-ext-install pdo pdo_pgsql pgsql

#Composer install
COPY --from=composer /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin



# WORKDIR /var/www/html
