FROM out001a/jupyter-notebook-base:latest
MAINTAINER out001a shanhuanming@foxmail.com

# env
ENV UBIN $HOME/bin
ENV GOPATH $HOME/go
ENV PATH $UBIN:$GOPATH/bin:$PATH

# golang
RUN yum -y install golang

# php 7.2
RUN yum -y install php72-php php72-php-mbstring php72-php-intl php72-php-pdo
RUN yum -y install php72-php-pecl-zmq php72-php-pecl-zip \
    php72-php-pecl-event php72-php-pecl-event php72-php-pecl-libsodium php72-php-pecl-uuid

# dependencies
RUN yum -y install git zeromq-devel which zip unzip

# change user
USER $USER
RUN mkdir $UBIN

# jupyter golang kernel
RUN go get -u github.com/pebbe/zmq4
RUN go get -u github.com/gopherdata/gophernotes
RUN mkdir -p $HOME/.local/share/jupyter/kernels/gophernotes
RUN cp $GOPATH/src/github.com/gopherdata/gophernotes/kernel/* $HOME/.local/share/jupyter/kernels/gophernotes

# jupyter php kernel
RUN ln -s $(which php72) $UBIN/php
RUN curl https://install.phpcomposer.com/installer -o /tmp/composer-setup.php
RUN php /tmp/composer-setup.php --install-dir=$UBIN --filename=composer && rm /tmp/composer-setup.php
RUN composer config -g repo.packagist composer https://packagist.phpcomposer.com
RUN curl https://litipk.github.io/Jupyter-PHP-Installer/dist/jupyter-php-installer.phar -o /tmp/jupyter-php-installer.phar
RUN php /tmp/jupyter-php-installer.phar install -v && rm /tmp/jupyter-php-installer.phar

USER root
