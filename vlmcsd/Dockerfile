FROM ubuntu

MAINTAINER Ivy Snow "ivy@sgri.net"

RUN true \
\
&& apt-get update \
&& apt-get dist-upgrade -y \
&& rm -rf /var/lib/apt/lists/*

COPY vlmcsd /usr/bin/

EXPOSE 1688

CMD ["/usr/bin/vlmcsd", "-f"]
