FROM magento/magento-cloud-docker-php:7.2-fpm

LABEL author "mariohdpz@gmail.com"

COPY etc/php-fpm.ini /usr/local/etc/php/conf.d/zz-magento.ini

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN useradd -m -d /home/magento2 -s /bin/bash magento2 \
    && adduser magento2 sudo \
    && passwd magento2 -d

WORKDIR /app

CMD ["php-fpm", "-R"]