FROM ubuntu:18.04

RUN echo "ZGViIGh0dHA6Ly9taXJyb3JzLmFsaXl1bi5jb20vdWJ1bnR1LyBiaW9uaWMgbWFpbiByZXN0cmljdGVkIHVuaXZlcnNlIG11bHRpdmVyc2UKZGViIGh0dHA6Ly9taXJyb3JzLmFsaXl1bi5jb20vdWJ1bnR1LyBiaW9uaWMtc2VjdXJpdHkgbWFpbiByZXN0cmljdGVkIHVuaXZlcnNlIG11bHRpdmVyc2UKZGViIGh0dHA6Ly9taXJyb3JzLmFsaXl1bi5jb20vdWJ1bnR1LyBiaW9uaWMtdXBkYXRlcyBtYWluIHJlc3RyaWN0ZWQgdW5pdmVyc2UgbXVsdGl2ZXJzZQpkZWIgaHR0cDovL21pcnJvcnMuYWxpeXVuLmNvbS91YnVudHUvIGJpb25pYy1wcm9wb3NlZCBtYWluIHJlc3RyaWN0ZWQgdW5pdmVyc2UgbXVsdGl2ZXJzZQpkZWIgaHR0cDovL21pcnJvcnMuYWxpeXVuLmNvbS91YnVudHUvIGJpb25pYy1iYWNrcG9ydHMgbWFpbiByZXN0cmljdGVkIHVuaXZlcnNlIG11bHRpdmVyc2UKZGViLXNyYyBodHRwOi8vbWlycm9ycy5hbGl5dW4uY29tL3VidW50dS8gYmlvbmljIG1haW4gcmVzdHJpY3RlZCB1bml2ZXJzZSBtdWx0aXZlcnNlCmRlYi1zcmMgaHR0cDovL21pcnJvcnMuYWxpeXVuLmNvbS91YnVudHUvIGJpb25pYy1zZWN1cml0eSBtYWluIHJlc3RyaWN0ZWQgdW5pdmVyc2UgbXVsdGl2ZXJzZQpkZWItc3JjIGh0dHA6Ly9taXJyb3JzLmFsaXl1bi5jb20vdWJ1bnR1LyBiaW9uaWMtdXBkYXRlcyBtYWluIHJlc3RyaWN0ZWQgdW5pdmVyc2UgbXVsdGl2ZXJzZQpkZWItc3JjIGh0dHA6Ly9taXJyb3JzLmFsaXl1bi5jb20vdWJ1bnR1LyBiaW9uaWMtcHJvcG9zZWQgbWFpbiByZXN0cmljdGVkIHVuaXZlcnNlIG11bHRpdmVyc2UKZGViLXNyYyBodHRwOi8vbWlycm9ycy5hbGl5dW4uY29tL3VidW50dS8gYmlvbmljLWJhY2twb3J0cyBtYWluIHJlc3RyaWN0ZWQgdW5pdmVyc2UgbXVsdGl2ZXJzZQ==" | base64 -d > /etc/apt/sources.list && \
    apt-get update && \
    apt-get -y install software-properties-common && \
    add-apt-repository ppa:ondrej/php && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install php7.0 && \
    chown www-data:www-data /var/www/html && \
    apt-get install -y vim && \
    apt-get -y install mysql-server && \
    apt-get install -y php7.0-mysql && \
    rm -f /var/www/html/index.html

# COPY files /tmp/files/
COPY src /var/www/html/

CMD  service apache2 start && service mysql start && \
 mysql -e "ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'smcq123';flush privileges;" -uroot -proot && \
 exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"

EXPOSE 80

#一些扩展需要自己按需安装