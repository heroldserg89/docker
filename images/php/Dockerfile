FROM php:8.2-fpm

RUN docker-php-ext-install pdo mysqli pdo_mysql

COPY --from=composer /usr/bin/composer /usr/bin/composer
ADD ./php.ini /usr/local/etc/php/conf.d/defaults.ini
RUN apt-get update && apt-get install -y \
    git \
    curl \
    zip \
    vim \
    unzip

ENTRYPOINT ["php-fpm"]
