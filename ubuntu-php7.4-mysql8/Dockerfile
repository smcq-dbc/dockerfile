FROM ubuntu:20.04

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install php && \
    chmod -R 777 /var/lib/php/sessions && \
    chown www-data:www-data /var/www/html && \
    apt-get install -y vim && \
    apt-get install -y mysql-server && \
    apt-get install -y php7.4-mysql && \
    echo "default_authentication_plugin=mysql_native_password" >> /etc/mysql/mysql.conf.d/mysqld.cnf

CMD  service mysql start && mysql -e "use mysql;update user set authentication_string = '' where user = 'root';ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'smcq123';" -uroot && service mysql restart && service apache2 start && export FLAG=not_flag && FLAG=not_flag && exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"

EXPOSE 80
