FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
    libzip-dev unzip git mariadb-client zlib1g-dev libicu-dev libonig-dev \
    && docker-php-ext-install pdo pdo_mysql intl zip opcache

# Install Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# Install Xdebug
RUN pecl channel-update pecl.php.net \
    && pecl install xdebug-3.1.6 \
    && docker-php-ext-enable xdebug

WORKDIR /var/www/symfony
