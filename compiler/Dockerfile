FROM ubuntu

MAINTAINER Ivy Snow "ivy@sgri.net"

RUN true \
\
&& apt-get update \
&& apt-get dist-upgrade -y \
\
&& apt-get install -y fish \
&& apt-get install -y vim \
&& apt-get install -y man \
&& apt-get install -y unzip \
&& apt-get install -y binutils \
&& apt-get install -y clang \
&& apt-get install -y libc++-dev \
&& apt-get install -y libc++abi-dev \
&& apt-get install -y make \
&& apt-get install -y scons --no-install-recommends \
&& apt-get install -y git --no-install-recommends \
&& apt-get install -y subversion --no-install-recommends \
\
&& rm -rf /var/lib/apt/lists/*

CMD ["/usr/bin/fish"]
