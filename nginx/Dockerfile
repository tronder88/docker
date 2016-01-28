FROM ubuntu

MAINTAINER Ivy Snow "ivy@sgri.net"

RUN true \
\
&& echo "deb http://nginx.org/packages/mainline/ubuntu/ wily nginx" > /etc/apt/sources.list.d/nginx.list \
&& echo "deb-src http://nginx.org/packages/mainline/ubuntu/ wily nginx" >> /etc/apt/sources.list.d/nginx.list \
&& apt-key --keyring /etc/apt/trusted.gpg.d/nginx.gpg adv --keyserver pgp.mit.edu --recv-keys 573BFD6B3D8FBC641079A6ABABF5BD827BD9BF62 \
\
&& apt-get update \
&& apt-get dist-upgrade -y \
\
&& apt-get install -y nginx \
\
&& usermod -a -G www-data nginx \
\
&& ln -sf /dev/stdout /var/log/nginx/access.log \
&& ln -sf /dev/stderr /var/log/nginx/error.log \
\
&& rm -rf /var/lib/apt/lists/*

VOLUME ["/var/www", "/etc/nginx/conf.d"]

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
