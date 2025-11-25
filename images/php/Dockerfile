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

RUN curl -OL https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar && \
    curl -OL https://squizlabs.github.io/PHP_CodeSniffer/phpcbf.phar && \
    chmod +x phpcs.phar phpcbf.phar && \
    mv phpcs.phar /usr/local/bin/phpcs && \
    mv phpcbf.phar /usr/local/bin/phpcbf

ENTRYPOINT ["php-fpm"]
