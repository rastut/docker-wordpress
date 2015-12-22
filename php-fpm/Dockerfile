FROM ubuntu:14.04.2
MAINTAINER Carles Lopez <litus81@gmail.com>

# Surpress Upstart errors/warning
RUN dpkg-divert --local --rename --add /sbin/initctl
RUN ln -sf /bin/true /sbin/initctl

# Let the conatiner know that there is no tty
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
apt-get install -y software-properties-common && \
apt-get upgrade -y && \ 
apt-get -y install php5-fpm \
                   php5-mysql \ 
                   php-apc \
                   php5-curl \
		   php5-gd   \
                   php5-intl \
                   php-pear \
                   php5-imagick \
                   php5-imap \
                   php5-mcrypt \
                   php5-memcache \
                   php5-memcached \
                   php5-ming \
                   php5-ps \
                   php5-pspell \ 
                   php5-recode \
                   php5-snmp \
                   php5-sqlite \
                   php5-tidy \
                   php5-xmlrpc php5-xsl
RUN sed -i '/^listen/c \
listen = 0.0.0.0:9000' /etc/php5/fpm/pool.d/www.conf
RUN sed -i -e "s/upload_max_filesize\s*=\s*2M/upload_max_filesize = 100M/g" /etc/php5/fpm/php.ini
RUN sed -i -e "s/post_max_size\s*=\s*8M/post_max_size = 100M/g" /etc/php5/fpm/php.ini
RUN sed -i -e "s/;daemonize\s*=\s*yes/daemonize = no/g" /etc/php5/fpm/php-fpm.conf
RUN find /etc/php5/cli/conf.d/ -name "*.ini" -exec sed -i -re 's/^(\s*)#(.*)/\1;\2/g' {} \;

EXPOSE 9000

ENTRYPOINT ["php5-fpm","-F"]
