FROM ubuntu:22.04

COPY . /laravel/CRM_DATA_GETTER

WORKDIR /laravel/CRM_DATA_GETTER/project

ENV DEBIAN_FRONTEND noninteractive
ENV TZ=UTC

EXPOSE 8001

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt update \ 
    && apt install -y php \
    && apt install -y php-cli unzip \
    && apt install -y curl \
    && apt install -y php-xml \
    && curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php \
    && php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer \
    && composer

CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port=8001"]