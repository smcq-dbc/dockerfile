FROM ubuntu:20.04

RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install php --fix-missing
RUN chown www-data:www-data /var/www/html
RUN apt-get install -y vim

CMD  service apache2 start && export FLAG=not_flag && FLAG=not_flag && exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"

EXPOSE 80
