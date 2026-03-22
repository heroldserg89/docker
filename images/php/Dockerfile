FROM php:8.4-fpm

RUN docker-php-ext-install pdo mysqli pdo_mysql

COPY --from=composer /usr/bin/composer /usr/bin/composer
ADD ./php.ini /usr/local/etc/php/conf.d/defaults.ini
RUN apt-get update && apt-get install -y \
    git \
    curl \
    zip \
    vim \
    unzip

ARG PHPCS_VERSION=4.0.1

RUN curl -OL https://github.com/PHPCSStandards/PHP_CodeSniffer/releases/download/${PHPCS_VERSION}/phpcs.phar&& \
    curl -OL https://github.com/PHPCSStandards/PHP_CodeSniffer/releases/download/${PHPCS_VERSION}/phpcbf.phar && \
    chmod +x phpcs.phar phpcbf.phar && \
    mv phpcs.phar /usr/local/bin/phpcs && \
    mv phpcbf.phar /usr/local/bin/phpcbf
RUN mkdir -p /var/log/php && chown -R www-data:www-data /var/log/php
ENTRYPOINT ["php-fpm"]
