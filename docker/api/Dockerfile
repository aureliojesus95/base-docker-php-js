FROM php:8.4-cli

WORKDIR /var/www

RUN apt-get update && apt-get install -y \
       git \
       unzip \
       zip \
       libzip-dev \
       libpq-dev \
    && docker-php-ext-install \
       pdo \
       pdo_mysql \
       bcmath \
       pcntl \
       exif \
       zip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

CMD ["tail", "-f", "/dev/null"]
# CMD ["php", "-S", "0.0.0.0:8080", "-t", "public"]