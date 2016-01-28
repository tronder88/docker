FROM ubuntu

MAINTAINER Ivy Snow "ivy@sgri.net"

RUN true \
\
&& apt-get update \
&& apt-get dist-upgrade -y \
\
&& apt-get install -y subversion \
&& apt-get install -y libsasl2-modules-sql \
\
&& rm -rf /var/lib/apt/lists/* \
\
&& mkdir -p /var/run/mysqld \
&& ln -s /tmp/mysqld.sock /var/run/mysqld/mysqld.sock

VOLUME ["/var/repos", "/usr/lib/sasl2"]

EXPOSE 3690

CMD ["svnserve", "-d", "--foreground", "--root=/var/repos"]
