FROM php:8.2-apache

# 設定ファイルのコピー
COPY config/000-default.conf /etc/apache2/sites-available/000-default.conf
COPY php.ini /usr/local/etc/php/

# 必要なパッケージのインストールと PHP 拡張の有効化
RUN apt-get update && apt-get install -y --no-install-recommends \
    zlib1g-dev \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    curl \
    nodejs \
    npm \
 && docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd \
 && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www/html