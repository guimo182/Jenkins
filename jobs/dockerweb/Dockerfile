FROM php:7.4-apache

# Habilitar mod rewrite y actualizar paquetes
RUN a2enmod rewrite \
    && apt-get update \
    && apt-get install -y \
        zlib1g-dev \
        libicu-dev \
        libxml2-dev \
        libpq-dev \
        libzip-dev \  # Instalar libzip necesario para la extensión zip
        zip \
        curl \
        vim \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_mysql pdo_pgsql zip intl xmlrpc soap opcache \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd

COPY . /var/www/html/
WORKDIR /var/www/html/
