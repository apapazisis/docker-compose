FROM php:7.2.14-fpm

RUN apt-get update

# Needed library for zip extension installation
RUN apt-get install zlib1g-dev -y 

# Needed library for gd extension installation
RUN apt-get install libpng-dev -y

# Needed library for xml extennsion installation
RUN apt-get install libxml2-dev -y

# Install PHP dependencies
RUN docker-php-ext-install -j$(nproc) \
    mysqli \
    pdo_mysql \
    mbstring \
    bcmath \
    zip \ 
    pcntl \
    gd \
    iconv \
    xml \
    ctype \
    json \
    tokenizer

# Install vim in php container
RUN apt-get install vim -y

# Install Composer in the PHP container so that it can be used from there
# Type => docker exec -it php7 /bin/bash to get into the PHP container and type => composer, normally you will see the composer commands
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer