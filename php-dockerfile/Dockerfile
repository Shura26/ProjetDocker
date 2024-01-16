FROM php:8.3-fpm

#RUN apt-get update && apt-get install -y npm nodejs curl git zip unzip \
#    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
COPY laravel /var/www/html/

RUN apt-get update && apt-get upgrade -y && apt-get install -y \
    npm \
    nodejs\
    git \
    curl \
    zip \
    unzip 

RUN docker-php-ext-install pdo_mysql


#RUN npm install -g create-vite
#RUN npm install vite



RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


WORKDIR /var/www/html

RUN composer update && composer install && npm install
CMD cd /var/www/html && npm run build && php artisan key:generate && php artisan migrate:fresh --seed
EXPOSE 80 3306

