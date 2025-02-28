FROM php:8.0-apache

# Instalar las dependencias necesarias para mysqli
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    && docker-php-ext-install mysqli

WORKDIR /var/www/html
COPY . .
EXPOSE 80
