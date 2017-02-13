FROM ubuntu:16.04


RUN apt update

RUN apt install nginx -y

RUN apt-get install -y nginx

ADD nginx.conf /etc/nginx/

# GET Arguments
ARG PHP_UPSTREAM=php-fpm
ARG PHPMYADMIN=phpmyadmin

RUN echo "upstream php-upstream { server ${PHP_UPSTREAM}:9000; }" > /etc/nginx/conf.d/upstream.conf

# Define working directory.
WORKDIR /etc/nginx

# Define default command.
CMD ["nginx"]

# Expose ports.
EXPOSE 80
EXPOSE 443
EXPOSE 6001
EXPOSE 6002