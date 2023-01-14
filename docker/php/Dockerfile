FROM php:8.1-apache

WORKDIR /var/www/html

RUN apt update -y \
  && curl -sL https://deb.nodesource.com/setup_current.x | bash - \
  && apt install -y unzip libpq-dev git vim nodejs \
  && pecl install xdebug \
  && docker-php-ext-enable xdebug \
  && docker-php-ext-install pgsql pdo_pgsql opcache \
  && a2enmod rewrite

COPY --from=composer /usr/bin/composer /usr/bin/composer

COPY ./000-default.conf /etc/apache2/sites-available/000-default.conf
COPY ./php.ini /usr/local/etc/php/php.ini
