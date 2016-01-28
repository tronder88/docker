FROM ubuntu

MAINTAINER Ivy Snow "ivy@sgri.net"

COPY entrypoint.sh /

ENV MYSQL_MAJOR 5.7

RUN true \
\
&& groupadd -r mysql \
&& useradd -r -g mysql mysql \
\
&& echo "deb http://repo.mysql.com/apt/ubuntu/ wily mysql-${MYSQL_MAJOR}" > /etc/apt/sources.list.d/mysql.list \
&& apt-key --keyring /etc/apt/trusted.gpg.d/mysql.gpg adv --keyserver ha.pool.sks-keyservers.net --recv-keys A4A9406876FCBD3C456770C88C718D3B5072E1F5 \
\
&& apt-get update \
&& apt-get dist-upgrade -y \
\
&& apt-get install -y pwgen \
\
&& { \
	echo mysql-community-server mysql-community-server/data-dir select ''; \
	echo mysql-community-server mysql-community-server/root-pass password ''; \
	echo mysql-community-server mysql-community-server/re-root-pass password ''; \
	echo mysql-community-server mysql-community-server/remove-test-db select false; \
} | debconf-set-selections \
&& apt-get install -y mysql-server --no-install-recommends \
\
&& sed -Ei 's/^(bind-address)/#&/' /etc/mysql/mysql.conf.d/mysqld.cnf \
&& sed -Ei 's/\/var\/run\/mysqld\/mysqld.sock/\/tmp\/mysqld.sock/g' /etc/mysql/mysql.conf.d/mysqld.cnf \
&& echo 'skip-host-cache\nskip-name-resolve' | awk '{ print } $1 == "[mysqld]" && c == 0 { c = 1; system("cat") }' /etc/mysql/mysql.conf.d/mysqld.cnf > /tmp/my.cnf \
&& mv /tmp/my.cnf /etc/mysql/mysql.conf.d/mysqld.cnf \
\
&& rm -rf /var/lib/mysql \
&& mkdir -p /var/lib/mysql \
\
&& rm -rf /var/lib/apt/lists/* \
\
&& mkdir -p /var/run/mysqld \
&& ln -s /tmp/mysqld.sock /var/run/mysqld/mysqld.sock

VOLUME ["/var/lib/mysql"]

EXPOSE 3306

ENTRYPOINT ["/entrypoint.sh"]
CMD ["mysqld"]
