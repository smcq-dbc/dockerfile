FROM ubuntu:20.04

RUN sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list \
&& apt-get update \
&& apt-get -y install software-properties-common \
&& add-apt-repository ppa:ondrej/php \
&& apt-get update \
&& DEBIAN_FRONTEND=noninteractive apt-get -y install php8.1 \
&& apt-get install -y vim \
&& chown www-data:www-data /var/www/html

CMD  service apache2 start && export FLAG=not_flag && FLAG=not_flag && exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"

EXPOSE 80