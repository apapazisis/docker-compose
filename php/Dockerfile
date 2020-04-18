FROM php:7.4.4-fpm

RUN apt-get update && apt-get install -y zlib1g-dev \
    libpng-dev \
    libxml2-dev \
    libssl-dev \
    vim \
    wget \
    curl \
    gnupg \
    libonig-dev \
    libzip-dev \
    libxrender1 \
    libfontconfig1 \
    libx11-dev \
    libjpeg62 \
    libxtst6 \
    supervisor
    
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
    tokenizer \
    calendar \
    soap \
    intl
    
RUN curl -sL https://deb.nodesource.com/setup_13.x | bash -
RUN apt-get install -y nodejs

RUN pecl install redis && docker-php-ext-enable redis

ENV WKHTML2PDF_VERSION 0.12.5
RUN wget "https://downloads.wkhtmltopdf.org/0.12/${WKHTML2PDF_VERSION}/wkhtmltox_${WKHTML2PDF_VERSION}-1.stretch_amd64.deb" \
&& apt-get install -y ./wkhtmltox_${WKHTML2PDF_VERSION}-1.stretch_amd64.deb 

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer config --global repo.packagist composer https://packagist.org
ENV PATH="$PATH:/root/.composer/vendor/bin"

RUN composer global require laravel/installer

COPY laravel-worker.conf /etc/supervisor/conf.d
CMD supervisord -c /etc/supervisor/conf.d/laravel-worker.conf
