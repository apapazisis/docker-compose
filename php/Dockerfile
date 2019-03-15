FROM php:7.2.14-fpm

RUN apt-get update && apt-get install -y zlib1g-dev \
    libpng-dev \
    libxml2-dev \
    libssl-dev \
    vim \
    wget \
    curl \
    gnupg
    
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
    soap
    
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN apt-get install -y \
    libxrender1 \
    libfontconfig1 \
    libx11-dev \
    libjpeg62 \
    libxtst6 \
    libssl1.0-dev 
    
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN apt-get install -y nodejs

ENV WKHTML2PDF_VERSION 0.12.5
RUN wget "https://downloads.wkhtmltopdf.org/0.12/${WKHTML2PDF_VERSION}/wkhtmltox_${WKHTML2PDF_VERSION}-1.stretch_amd64.deb" \
&& apt-get install -y ./wkhtmltox_${WKHTML2PDF_VERSION}-1.stretch_amd64.deb 
