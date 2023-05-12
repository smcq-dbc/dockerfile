FROM ubuntu:20.04

RUN apt-get update
RUN apt-get -y install software-properties-common --fix-missing
RUN add-apt-repository ppa:ondrej/php 
RUN apt-get update 
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install php7.0 
RUN apt-get install -y vim 
RUN chown www-data:www-data /var/www/html

CMD  service apache2 start && export FLAG=not_flag && FLAG=not_flag && exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"

EXPOSE 80