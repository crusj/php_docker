FROM php:7.3-fpm-stretch

##### 替换为阿里源
RUN sed -i "s/deb.debian.org/mirrors.aliyun.com/g;s/security.debian.org/mirrors.aliyun.com/g" /etc/apt/sources.list  \
&&  cd /etc/apt/sources.list.d && if [ "$(ls)" ]; then  ls | xargs  sed -i "s/deb.debian.org/mirrors.aliyun.com/g;s/security.debian.org/mirrors.aliyun.com/g"; fi \
&&  apt update
##### 安装系统软件

RUN apt install -y vim net-tools telnet wget libxml2-dev zlib1g-dev libzip-dev unzip libpng-dev libjpeg-dev libfreetype6-dev 

##### 安装php扩展

RUN docker-php-ext-configure gd --with-jpeg-dir=/usr/include/ --with-freetype-dir=/usr/include/ \ 
&& docker-php-ext-install pdo_mysql soap zip gd mysqli bcmath \
&& pecl install redis mongodb xdebug  \
&& docker-php-ext-enable pdo_mysql soap zip redis mongodb gd mysqli bcmath

##### 安装composer

RUN wget https://getcomposer.org/download/1.8.5/composer.phar -O /usr/local/bin/composer \
&& chmod +x /usr/local/bin/composer  \
&& composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/
##### 改变www-data uid gid
RUN usermod -u 1000 www-data && groupmod -g 1000 www-data &&  cp $PHP_INI_DIR/php.ini-production $PHP_INI_DIR/php.ini

COPY xdebug.ini /usr/local/etc/php/conf.d



