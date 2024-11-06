FROM php:8.2-apache
# COPY ./php.ini /usr/local/etc/php/
# Composerのインストール
# zipとunzip、そしてgitをインストール
# RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer



RUN apt-get update && apt-get install -y \
    zip \
    unzip \
    git \
    default-mysql-client \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libicu-dev \
    libonig-dev \
    libzip-dev \
    imagemagick\
    libmagickwand-dev \
    && docker-php-ext-install pdo_mysql mysqli gd iconv intl zip \
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    && a2enmod rewrite


RUN apt-get update && apt-get install -y \
    default-mysql-client \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Composerを直接ダウンロードしてインストール
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# 権限の設定
RUN chown -R www-data:www-data /var/www/html
RUN chmod -R 775 /var/www/html
