FROM ubuntu

MAINTAINER Ivy Snow "ivy@sgri.net"

RUN true \
\
&& apt-get update \
&& apt-get dist-upgrade -y \
\
&& apt-get install -y libtalloc2 \
&& apt-get install -y libssl1.0.0 \
&& apt-get install -y libpcap0.8 \
&& apt-get install -y libiodbc2 \
&& apt-get install -y libmysqlclient18 \
&& apt-get install -y libpq5 \
&& apt-get install -y libsqlite3-0 \
\
&& mkdir -p /var/log/radius \
\
&& rm -rf /var/lib/apt/lists/* \
\
&& mkdir -p /var/run/mysqld \
&& ln -s /tmp/mysqld.sock /var/run/mysqld/mysqld.sock

ADD freeradius-server-3.0.10-bin.tar.bz2 /usr/local/

VOLUME ["/usr/local/freeradius/etc/raddb"]

EXPOSE 1812/udp 1813/udp

CMD ["/usr/local/freeradius/sbin/radiusd", "-f"]
