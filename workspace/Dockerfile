FROM ubuntu:16.04

RUN apt update -y && apt install curl vim git -y


# Install NodeJS and Yarn
RUN curl -sL https://deb.nodesource.com/setup_6.x | bash  && apt-get install -y nodejs

RUN curl -o- -L https://yarnpkg.com/install.sh | bash


# Add the "PHP 7" ppa
RUN apt-get install -y software-properties-common && \
    add-apt-repository -y ppa:ondrej/php

RUN apt-get update && \
    apt-get install -y --force-yes \
        php7.1-cli

USER root

ADD .vimrc /root

