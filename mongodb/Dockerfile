FROM ubuntu

MAINTAINER Ivy Snow "ivy@sgri.net"

COPY entrypoint.sh /
COPY gosu-amd64 /usr/bin/gosu

ENV MONGODB_MAJOR 3.2

RUN true \
\
&& groupadd -r mongodb \
&& useradd -r -g mongodb mongodb \
\
&& echo "deb http://repo.mongodb.org/apt/ubuntu/ trusty/mongodb-org/${MONGODB_MAJOR} multiverse" > /etc/apt/sources.list.d/mongodb.list \
&& apt-key --keyring /etc/apt/trusted.gpg.d/mongodb.gpg adv --keyserver ha.pool.sks-keyservers.net --recv-keys 42F3E95A2C4F08279C4960ADD68FA50FEA312927 \
\
&& apt-get update \
&& apt-get dist-upgrade -y \
\
&& apt-get install -y numactl \
\
&& apt-get install -y mongodb-org mongodb-org-server --no-install-recommends \
\
&& mkdir -p /data/db \
\
&& rm -rf /var/lib/apt/lists/*

VOLUME ["/data/db"]

EXPOSE 27017

ENTRYPOINT ["/entrypoint.sh"]
CMD ["mongod", "--filePermissions", "0777"]
