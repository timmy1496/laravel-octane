FROM php:latest
RUN apt-get update && apt-get upgrade -y && apt-get install git -y

# Install Extensions (Swoole)
ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
RUN chmod +x /usr/local/bin/install-php-extensions && sync
RUN install-php-extensions swoole

# Install Source Code Dependencies
ADD https://getcomposer.org/composer-stable.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer

RUN docker-php-ext-configure pcntl --enable-pcntl
RUN docker-php-ext-install pcntl

# Open Ports
EXPOSE 8000

# Entrypoint
WORKDIR /app
ENTRYPOINT ["php", "artisan", "octane:start", "--host=0.0.0.0"]