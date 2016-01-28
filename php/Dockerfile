FROM ubuntu

MAINTAINER Ivy Snow "ivy@sgri.net"

RUN true \
\
&& echo "deb http://ppa.launchpad.net/ondrej/php/ubuntu wily main" > /etc/apt/sources.list.d/php.list \
&& apt-key --keyring /etc/apt/trusted.gpg.d/php.gpg adv --keyserver keyserver.ubuntu.com --recv-keys 14AA40EC0831756756D7F66C4F4EA0AAE5267A6C \
\
&& apt-get update \
&& apt-get dist-upgrade -y \
\
&& apt-get install -y php-fpm \
&& apt-get install -y php-amqp \
&& apt-get install -y php-apcu \
&& apt-get install -y php-ast \
&& apt-get install -y php-bz2 \
&& apt-get install -y php-curl \
&& apt-get install -y php-gd \
&& apt-get install -y php-gmp \
&& apt-get install -y php-imagick \
&& apt-get install -y php-imap \
&& apt-get install -y php-intl \
&& apt-get install -y php-ldap \
&& apt-get install -y php-mcrypt \
&& apt-get install -y php-memcached \
&& apt-get install -y php-mongodb \
&& apt-get install -y php-mysql \
&& apt-get install -y php-pgsql \
&& apt-get install -y php-pspell \
&& apt-get install -y php-recode \
&& apt-get install -y php-redis \
&& apt-get install -y php-sqlite3 \
&& apt-get install -y php-ssh2 \
&& apt-get install -y php-sybase \
&& apt-get install -y php-tidy \
&& apt-get install -y php-uuid \
&& apt-get install -y php-xmlrpc \
&& apt-get install -y php-xsl \
\
&& sed -Ei 's/\/run\/php\/php7.0-fpm.sock/\/tmp\/php7.0-fpm.sock/g' /etc/php/7.0/fpm/pool.d/www.conf \
\
&& mkdir /run/php \
\
&& rm -rf /var/lib/apt/lists/* \
\
&& mkdir -p /var/run/mysqld \
&& ln -s /tmp/mysqld.sock /var/run/mysqld/mysqld.sock

CMD ["php-fpm7.0", "-F"]
