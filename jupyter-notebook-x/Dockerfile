FROM out001a/jupyter-notebook-linguist:latest
MAINTAINER out001a shanhuanming@foxmail.com

# yum
RUN yum -y install vim less net-tools
RUN yum -y groups mark convert
RUN yum -y groupinstall "Development Tools"

# python opencv
RUN yum -y install libSM libXrender libXext
RUN pip install opencv-python

# php extensions
RUN yum -y install php72-php-pear php72-php-fpm php72-php-mysqlnd
RUN yum -y install php72-php-pecl-yaf php72-php-pecl-swoole php72-php-pecl-redis

# others
RUN cp /usr/share/zoneinfo/PRC /etc/localtime
