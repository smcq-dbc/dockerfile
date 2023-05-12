FROM ubuntu:18.04

RUN apt-get update && \
    apt-get -y install software-properties-common && \
    add-apt-repository ppa:ondrej/php && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install php7.4 && \
    chown www-data:www-data /var/www/html && \
    apt-get install -y vim && \
    apt-get -y install mysql-server && \
    apt-get install -y php7.4-mysql && \
    rm -f /var/www/html/index.html

# COPY files /tmp/files/
COPY src /var/www/html/

CMD  service apache2 start && service mysql start && \
 mysql -e "ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'smcq123';flush privileges;" -uroot && \
 service mysql restart && export FLAG=not_flag && FLAG=not_flag && exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"

EXPOSE 80

#一些扩展需要自己按需安装