FROM php:7.3-fpm

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
    apt-get -y install \
        apt-utils \
        g++ \
        unzip \
        libicu-dev \
        libpq-dev

RUN docker-php-ext-configure \
    pgsql -with-pgsql=/usr/local/pgsql

RUN docker-php-ext-install \
    intl \
    pdo \
    pdo_pgsql

RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

COPY php-fpm.conf /usr/local/etc/php-fpm.d/
COPY php.ini /usr/local/etc/php/

ARG WORK_DIR

WORKDIR ${WORK_DIR}

ARG USER_ID

RUN apt-get update -yq \
    && apt-get install curl gnupg -yq \
    && curl -sL https://deb.nodesource.com/setup_10.x | bash \
    && apt-get install nodejs -yq

RUN mkdir /.config
RUN mkdir /.npm
RUN chown -R $USER_ID:$USER_ID /.config
RUN chown -R $USER_ID:$USER_ID /.npm

RUN touch /.npmrc
RUN chown -R $USER_ID:$USER_ID /.npmrc
ENV NPM_CONFIG_USERCONFIG=/.npmrc

RUN npm config set prefix ${WORK_DIR}/webroot

RUN curl -sS https://getcomposer.org/installer | \
  php -- --install-dir=/usr/local/bin --filename=composer

# ENV COMPOSER_HOME /composer

# COPY composer/auth.json /composer/auth.json
# RUN chown -R ${USER_ID} $COMPOSER_HOME

# ARG GITHUB_OAUTH
# RUN sed -i.bak "s|GITHUB_OAUTH|${GITHUB_OAUTH}|g" /composer/auth.json

USER $USER_ID
