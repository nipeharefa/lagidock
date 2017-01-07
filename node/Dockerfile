FROM ubuntu:16.04


RUN apt update

RUN apt install curl vim git inetutils-ping -y

RUN curl -sL https://deb.nodesource.com/setup_6.x | bash -

RUN apt-get install -y nodejs

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -

RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt update && apt install yarn -y

RUN npm install -g laravel-echo-server
RUN npm install -g pm2


# Define working directory.
WORKDIR /var/www

EXPOSE 3000
EXPOSE 6001