FROM php:8.3.7-fpm

ENV TZ Asia/Tokyo

RUN apt-get update
RUN apt-get install -y  \
    git  \
    unzip \
    libbz2-dev \
    libzip-dev \
    libicu-dev \
    libonig-dev \
    libffi-dev \
    libpng-dev \
    libpq-dev \
    libgmp3-dev \
    libc-client-dev \
    libkrb5-dev \
    libldap2-dev \
    libpspell-dev \
    libsnmp-dev \
    libxml2-dev \
    libtidy-dev \
    libxslt-dev

RUN docker-php-ext-configure imap --with-kerberos --with-imap-ssl
RUN docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu

RUN docker-php-ext-install bcmath
RUN docker-php-ext-install calendar
RUN docker-php-ext-install ctype
RUN docker-php-ext-install dom
RUN docker-php-ext-install exif
RUN docker-php-ext-install ffi
RUN docker-php-ext-install fileinfo
RUN docker-php-ext-install ftp
RUN docker-php-ext-install gettext

RUN docker-php-ext-install iconv
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install opcache
RUN docker-php-ext-install pcntl
RUN docker-php-ext-install pdo_pgsql
RUN docker-php-ext-install posix
RUN docker-php-ext-install session
RUN docker-php-ext-install shmop

RUN docker-php-ext-install simplexml
RUN docker-php-ext-install sockets
RUN docker-php-ext-install sysvmsg
RUN docker-php-ext-install sysvsem
RUN docker-php-ext-install sysvshm
RUN docker-php-ext-install xsl
RUN docker-php-ext-install zip

# php.ini
COPY ./container/laravel/php.ini $PHP_INI_DIR/conf.d/php.ini

# composer
COPY --from=composer /usr/bin/composer /usr/bin/composer

# node(バージョン指定) npm をインストール
RUN apt-get install -y nodejs npm
RUN npm install n -g
RUN n 20.14.0
RUN apt purge -y nodejs npm
RUN apt -y autoremove

WORKDIR /usr/home/clair/project