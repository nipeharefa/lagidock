FROM ubuntu:16.04

RUN apt update -y && apt install curl vim git -y


# Install NodeJS and Yarn
RUN curl -sL https://deb.nodesource.com/setup_6.x | bash  && apt-get install -y nodejs

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

# Add the "PHP 7" ppa
RUN apt-get install -y software-properties-common && \
    add-apt-repository -y ppa:ondrej/php

RUN apt-get update && \
    apt-get install -y --force-yes \
        php7.1-cli

RUN apt install -y --force-yes php7.1-common php7.1-curl php7.1-json php7.1-xml php7.1-mbstring

RUN apt install -y --force-yes php7.1-mysql \
        php7.1-pgsql \
        php7.1-sqlite \
        php7.1-sqlite3 \
        php7.1-zip \
        php7.1-bcmath \
        php7.1-memcached \
        php7.1-gd

RUN apt install -y --force-yes git vim curl inetutils-ping

RUN curl -sL https://deb.nodesource.com/setup_6.x | bash -

RUN apt-get install -y nodejs

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -

RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4F4EA0AAE5267A6C

RUN apt update && apt install yarn -y

RUN npm install -g gulp

RUN apt clean

USER root

ADD .vimrc /root

WORKDIR /var/www