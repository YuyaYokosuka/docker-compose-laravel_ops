FROM php:7.1.0-fpm-alpine
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer  \
    && docker-php-ext-install pdo_mysql mysqli mbstring
