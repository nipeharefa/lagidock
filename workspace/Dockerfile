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

USER root

ADD .vimrc /root

