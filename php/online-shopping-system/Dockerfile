FROM php:7.4-apache
RUN apt-get update -y && \
    apt-get install -y curl && \
    docker-php-ext-install mysqli
EXPOSE 80
