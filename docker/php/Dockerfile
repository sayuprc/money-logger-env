FROM php:8.1-apache

WORKDIR /var/www/html

RUN curl -sL https://deb.nodesource.com/setup_current.x | bash - \
  && curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - \
  && echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list \
  && apt update -y \
  && apt install -y unzip libpq-dev git vim nodejs yarn \
  && pecl install xdebug \
  && docker-php-ext-enable xdebug \
  && docker-php-ext-install pgsql pdo_pgsql opcache \
  && a2enmod rewrite

COPY --from=composer /usr/bin/composer /usr/bin/composer
