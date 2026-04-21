FROM php:8.4-cli

ARG GID=1000
ARG UID=1000
ARG USERNAME=dev

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
    && groupadd -g ${GID} ${USERNAME} \
    && useradd -u ${UID} -g ${GID} -m -s /bin/bash ${USERNAME} \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

USER ${USERNAME}

CMD ["tail", "-f", "/dev/null"]
