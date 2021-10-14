FROM php:7.4-fpm-alpine

LABEL maintainer="Get In <diego.mosela@getinapp.com.br>"

ENV ASUSER=0

RUN apk upgrade \
    && apk add --no-cache --virtual .build-deps \
		$PHPIZE_DEPS \
        oniguruma-dev \
        libstdc++ \
        zlib-dev \
        linux-headers \
    && apk add --no-cache \
		git \
        unzip \
        openssl \
        libzip-dev \
        libstdc++ \
        libstdc++6 \
        libpng-dev \
    && pecl install \
        redis \
        grpc \
        xdebug \
    && docker-php-ext-enable \
        redis \
        grpc \
        xdebug \
    && docker-php-ext-install \
        zip \
        pdo_mysql \
        mbstring \
        bcmath \
        opcache \
        sockets \
        exif \
        pcntl \
        gd \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && apk del -f .build-deps

COPY ./xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
COPY user-entrypoint /usr/local/bin/
RUN chmod +x /usr/local/bin/user-entrypoint

WORKDIR /var/www

ENTRYPOINT ["user-entrypoint"]

CMD ["php-fpm"]

EXPOSE 9000