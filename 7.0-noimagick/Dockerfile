FROM php:7.0-cli

RUN apt-get update && \
  DEBIAN_FRONTEND=noninteractive apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng12-dev \
    libbz2-dev \
  && rm -r /var/lib/apt/lists/*

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install mysqli gd pdo_mysql

RUN pecl install -o -f redis \
  &&  rm -rf /tmp/pear \
  &&  echo "extension=redis.so" > /usr/local/etc/php/conf.d/redis.ini

RUN echo "date.timezone=Europe/Prague" > /usr/local/etc/php/conf.d/datetime.ini
RUN echo "memory_limit=-1" > /usr/local/etc/php/conf.d/memory_limit.ini
