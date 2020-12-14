FROM php:7.2.6-apache

COPY ./app/ /var/www/html
COPY ./docker/vhost.conf /etc/apache2/sites-available/000-default.conf

WORKDIR /var/www/html

RUN rm /etc/apt/preferences.d/no-debian-php && \
    apt-get update -y \
    && apt-get install -y \
    libxml2-dev \
    php7.0-soap \
    && apt-get clean -y \
    && docker-php-ext-install soap mbstring pdo pdo_mysql bcmath \
    && chown -R www-data:www-data /var/www/html \
    && a2enmod rewrite && service apache2 restart