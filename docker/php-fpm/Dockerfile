FROM php:7.3-fpm-alpine

COPY docker/php-fpm/wait-for-it.sh /usr/bin/wait-for-it

RUN chmod +x /usr/bin/wait-for-it

RUN apk --update --no-cache add \
    git unzip zip nodejs yarn \
    # xml
    libxml2-dev \
    libxslt-dev \
    # intl
    icu-dev \
    # curl
    curl-dev libcurl \
    # gd
    libwebp-dev libjpeg-turbo-dev libpng-dev \
    # zip
    libzip-dev \
    oniguruma-dev

RUN docker-php-ext-install pdo_mysql mysqli xml xsl mbstring intl curl gd zip

COPY --from=composer /usr/bin/composer /usr/bin/composer

WORKDIR /var/www
COPY app /var/www/app

# CMD composer install ; wait-for-it database:3306 -- bin/console ezplatform:install clean ;  php-fpm 
CMD php-fpm 

EXPOSE 9000
