FROM phpdockerio/php:8.1-fpm

ENV PHP_IDE_CONFIG serverName=php_backend

RUN apt-get update && apt-get -y upgrade

RUN apt-get update \
    && apt-get -y --no-install-recommends install \
        php8.1-mysql php8.1-redis \
        wget git unzip mc less nano \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

ARG INSTALL_XDEBUG=false
RUN if [ ${INSTALL_XDEBUG} = true ]; then \
    # Install the xdebug extension
    apt-get update \
        && apt-get -y --no-install-recommends install php8.1-xdebug \
        && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/* \
;fi

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

# Install Symfony
RUN wget https://get.symfony.com/cli/installer -O - | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony

COPY wait-for-it.sh /wait-for-it.sh

WORKDIR "/var/www/adrianoff/php_backend"