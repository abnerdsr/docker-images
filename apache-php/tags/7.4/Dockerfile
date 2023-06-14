FROM php:7.4-apache

LABEL maintainer="Acessórias"

WORKDIR /var/www/html

# Altera o timezone do linux
ENV TZ="America/Sao_Paulo"
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Atualiza o linux para versão mais recente
RUN apt-get update -y && apt-get upgrade -y && apt-get autoremove -y && apt-get clean

# instala as bibliotecas essenciais que necessitam para os pacotes do composer
RUN apt-get install -y curl zip unzip git gnupg gosu libcap2-bin libpng-dev libonig-dev python2 libcurl4-openssl-dev libxml2-dev libzip-dev
# instala as extensões do php que serão utilizadas
RUN docker-php-ext-install mysqli pdo curl xml intl gd zip mbstring

# Composer 2.x e Node 18.x (node, npm, npx e yarn)
RUN php -r "readfile('https://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer \
    && curl -sLS https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs \
    && npm install -g npm \
    && curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | tee /usr/share/keyrings/yarn.gpg >/dev/null \
    && echo "deb [signed-by=/usr/share/keyrings/yarn.gpg] https://dl.yarnpkg.com/debian/ stable main" > /etc/apt/sources.list.d/yarn.list \
    && apt-get install -y yarn \
    && apt-get -y autoremove \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*