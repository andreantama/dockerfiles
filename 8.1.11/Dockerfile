# bcmath bz2 calendar ctype curl dba dom enchant exif ffi fileinfo filter ftp gd gettext gmp hash iconv imap intl json ldap mbstring mysqli oci8 odbc opcache pcntl pdo pdo_dblib pdo_firebird pdo_mysql pdo_oci pdo_odbc pdo_pgsql pdo_sqlite pgsql phar posix pspell readline reflection session shmop simplexml snmp soap sockets sodium spl standard sysvmsg sysvsem sysvshm tidy tokenizer xml xmlreader xmlrpc xmlwriter xsl zend_test zip

#FROM andreantama/php:7.4.22-apache-simregs
FROM php:8.1.11-apache
RUN apt-get update
RUN apt-get install -y libldb-dev libldap2-dev git zip curl sudo unzip libcurl4-openssl-dev libicu-dev \
	libbz2-dev libpng-dev libjpeg-dev libmcrypt-dev libreadline-dev libfreetype6-dev g++ \
	libzip-dev postgresql-server-dev-all libxml2 libxml2-dev libonig-dev nano \
	&& apt-get clean

#RUN docker-php-source extract

RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install pdo_pgsql

 RUN docker-php-ext-install ldap curl pdo pdo_pgsql gd zip bz2 \
 	intl bcmath opcache calendar pdo_mysql

RUN a2enmod rewrite headers
ENV LOG_CHANNEL=stderr
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
# RUN mkdir /var/www/private

# RUN rm -r /var/www/private/vendor
# RUN rm -r /var/www/private/bootstrap
# RUN rm -r /var/www/private/storage
# RUN rm /var/www/private/composer.json
# RUN rm /var/www/private/composer.lock

#COPY composer.json /var/www/private/composer.json
#COPY composer.lock /var/www/private/composer.lock
#COPY artisan /var/www/private

# COPY . /var/www/private
# RUN composer update --working-dir ../private
