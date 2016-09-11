FROM alpine:3.4
MAINTAINER smizy

RUN set -x \
    && apk --no-cache --update add \
        php5-curl \
        php5-ctype \
        php5-dom \
        php5-fpm \
        php5-intl \
        php5-json \
        php5-mysql \
        php5-opcache \
        php5-openssl \
        php5-pdo_mysql \
        php5-pdo_pgsql \
        php5-phar \
        php5-xml \
        php5-zip \
        php5-zlib \
        su-exec \
        wget \
    && adduser -D  -g '' -s /sbin/nologin -u 1000 docker \
    && wget -q -O - https://getcomposer.org/installer \
         | php --  --install-dir=/usr/local/bin --filename=composer 

WORKDIR /var/www/html

EXPOSE 9000
CMD ["su-exec", "nobody", "php", "-S", "0.0.0.0:9000"]