FROM ubuntu:16.04


RUN apt update

RUN apt install nginx -y

RUN apt-get install -y nginx

ADD nginx.conf /etc/nginx/

# RUN adduser -D -H -u 1000 -s /bin/bash www-data

# Define working directory.
WORKDIR /etc/nginx

# Define default command.
CMD ["nginx"]

# Expose ports.
EXPOSE 80
EXPOSE 443