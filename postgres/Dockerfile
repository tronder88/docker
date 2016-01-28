FROM ubuntu

MAINTAINER Ivy Snow "ivy@sgri.net"

COPY entrypoint.sh /
COPY gosu-amd64 /usr/bin/gosu

ENV PG_MAJOR 9.5

RUN true \
\
&& groupadd -r postgres \
&& useradd -r -g postgres postgres \
\
&& echo "deb http://apt.postgresql.org/pub/repos/apt/ wily-pgdg main ${PG_MAJOR}" > /etc/apt/sources.list.d/postgres.list \
&& apt-key --keyring /etc/apt/trusted.gpg.d/postgres.gpg adv --keyserver ha.pool.sks-keyservers.net --recv-keys B97B0AFCAA1A47F044F244A07FCC7D46ACCC4CF8 \
\
&& apt-get update \
&& apt-get dist-upgrade -y \
\
&& apt-get install -y postgresql-common --no-install-recommends \
&& sed -ri 's/#(create_main_cluster) .*$/\1 = false/' /etc/postgresql-common/createcluster.conf \
\
&& apt-get install -y postgresql-$PG_MAJOR \
\
&& rm -rf /var/lib/apt/lists/* \
\
&& mkdir -p /run/postgresql \
&& ln -s /tmp/.s.PGSQL.5432 /run/postgresql/.s.PGSQL.5432

ENV PATH /usr/lib/postgresql/$PG_MAJOR/bin:$PATH
ENV PGDATA /var/lib/postgresql/data

VOLUME ["/var/lib/postgresql/data"]

EXPOSE 5432

ENTRYPOINT ["/entrypoint.sh"]
CMD ["postgres"]
