FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
        libonig-dev \
        libfreetype6-dev libjpeg62-turbo-dev \
        libpng-dev libbz2-dev \
        libssl-dev autoconf \
        ca-certificates curl g++ libicu-dev \
        libmagickwand-dev mariadb-client libzip-dev\
        && \
        pecl install imagick-3.4.3 \
        && \
        docker-php-ext-install \
        bcmath bz2 exif \
        ftp gd gettext mbstring opcache \
        shmop sockets sysvmsg sysvsem sysvshm \
        zip iconv pdo_mysql intl \
        && \
        docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
        && \
        docker-php-ext-enable imagick

RUN docker-php-ext-install soap

RUN echo "upload_max_filesize = 128M" > /usr/local/etc/php/php.ini && \
    echo "post_max_size = 128M" >> /usr/local/etc/php/php.ini && \
    echo "max_execution_time = 300" >> /usr/local/etc/php/php.ini && \
    echo "memory_limit = 256M" >> /usr/local/etc/php/php.ini

COPY --chown=www-data:www-data ./src /var/www/html