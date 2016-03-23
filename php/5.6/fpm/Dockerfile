FROM php:5-fpm
MAINTAINER out001a@gmail.com

RUN apt-get update && apt-get -y upgrade
RUN apt-get -y install apt-utils libssl-dev libmagickwand-dev

# ENV CONF_DIR /usr/local/etc/php/conf.d
# RUN pecl install redis            && echo extension=redis.so   > ${CONF_DIR}/redis.ini
# RUN pecl install mongo            && echo extension=mongo.so   > ${CONF_DIR}/mongo.ini
# RUN pecl install imagick          && echo extension=imagick.so > ${CONF_DIR}/imagick.ini
# RUN pecl install msgpack-0.5.7    && echo extension=msgpack.so > ${CONF_DIR}/msgpack.ini

RUN pecl install redis           && docker-php-ext-enable redis
RUN pecl install mongo           && docker-php-ext-enable mongo
RUN pecl install imagick         && docker-php-ext-enable imagick
RUN pecl install msgpack-0.5.7   && docker-php-ext-enable msgpack

RUN docker-php-ext-install -j$(nproc) opcache
# TODO: config opcache.ini

COPY ./app/ /var/www/html/

## nginx server conf
# server {
#     listen      8088;
# 
#     root        /var/www/html;
# 
#     access_log  /data/ngx/logs/access.log  main;
#     error_log   /data/ngx/logs/error.log  debug;
# 
#     location ~ \.php(.*)$ {
#         fastcgi_pass   127.0.0.1:9001;
#         fastcgi_index  index.php;
#         include        fastcgi.conf;
#         #fastcgi_split_path_info ^(.+\.php)(.*)$;
#     }
# }
