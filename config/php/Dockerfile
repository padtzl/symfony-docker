FROM php:8.3-fpm
RUN apt-get update && apt-get install -y libpq-dev git unzip curl \
    && docker-php-ext-install pdo pdo_pgsql
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
WORKDIR /app
COPY config/php/php.ini /usr/local/etc/php/conf.d/docker-php-config.ini
RUN curl -sS https://get.symfony.com/cli/installer | bash && \
    mv /root/.symfony*/bin/symfony /usr/local/bin/symfony
EXPOSE 9000
CMD ["php-fpm"]
