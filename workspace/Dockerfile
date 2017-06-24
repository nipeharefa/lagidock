FROM ubuntu:16.04

RUN apt-get clean && apt-get update
RUN apt-get install locales curl vim git -y
RUN locale-gen en_US.UTF-8

# RUN apt install curl vim git -y


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

# Install composer and add its bin to the PATH.

# Install composer and add its bin to the PATH.
RUN curl -s http://getcomposer.org/installer | php && \
    echo "export PATH=${PATH}:/var/www/vendor/bin" >> ~/.bashrc && \
    mv composer.phar /usr/local/bin/composer

# Clean up
USER root
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install Imagick.
RUN apt update && apt-get install -y \
    libmagickwand-dev

RUN apt install -y --force-yes php-dev
RUN pecl install imagick

USER root

RUN apt install php-imagick openssh-server -y

ADD insecure_id_rsa /tmp/id_rsa
ADD insecure_id_rsa.pub /tmp/id_rsa.pub

RUN mkdir /root/.ssh/
RUN rm -f /etc/service/sshd/down && \
    cat /tmp/id_rsa.pub >> /root/.ssh/authorized_keys \
        && cat /tmp/id_rsa.pub >> /root/.ssh/id_rsa.pub \
        && cat /tmp/id_rsa >> /root/.ssh/id_rsa \
        && rm -f /tmp/id_rsa* \
        && chmod 644 /root/.ssh/authorized_keys /root/.ssh/id_rsa.pub \
    && chmod 400 /root/.ssh/id_rsa

EXPOSE 22