FROM ubuntu:20.04

RUN echo "ZGViIGh0dHA6Ly9taXJyb3JzLmFsaXl1bi5jb20vdWJ1bnR1LyBmb2NhbCBtYWluIHJlc3RyaWN0ZWQgdW5pdmVyc2UgbXVsdGl2ZXJzZSAKCmRlYiBodHRwOi8vbWlycm9ycy5hbGl5dW4uY29tL3VidW50dS8gZm9jYWwtc2VjdXJpdHkgbWFpbiByZXN0cmljdGVkIHVuaXZlcnNlIG11bHRpdmVyc2UgCgpkZWIgaHR0cDovL21pcnJvcnMuYWxpeXVuLmNvbS91YnVudHUvIGZvY2FsLXVwZGF0ZXMgbWFpbiByZXN0cmljdGVkIHVuaXZlcnNlIG11bHRpdmVyc2UgCgpkZWIgaHR0cDovL21pcnJvcnMuYWxpeXVuLmNvbS91YnVudHUvIGZvY2FsLXByb3Bvc2VkIG1haW4gcmVzdHJpY3RlZCB1bml2ZXJzZSBtdWx0aXZlcnNlIAoKZGViIGh0dHA6Ly9taXJyb3JzLmFsaXl1bi5jb20vdWJ1bnR1LyBmb2NhbC1iYWNrcG9ydHMgbWFpbiByZXN0cmljdGVkIHVuaXZlcnNlIG11bHRpdmVyc2UgCgpkZWItc3JjIGh0dHA6Ly9taXJyb3JzLmFsaXl1bi5jb20vdWJ1bnR1LyBmb2NhbCBtYWluIHJlc3RyaWN0ZWQgdW5pdmVyc2UgbXVsdGl2ZXJzZSAKCmRlYi1zcmMgaHR0cDovL21pcnJvcnMuYWxpeXVuLmNvbS91YnVudHUvIGZvY2FsLXNlY3VyaXR5IG1haW4gcmVzdHJpY3RlZCB1bml2ZXJzZSBtdWx0aXZlcnNlIAoKZGViLXNyYyBodHRwOi8vbWlycm9ycy5hbGl5dW4uY29tL3VidW50dS8gZm9jYWwtdXBkYXRlcyBtYWluIHJlc3RyaWN0ZWQgdW5pdmVyc2UgbXVsdGl2ZXJzZSAKCmRlYi1zcmMgaHR0cDovL21pcnJvcnMuYWxpeXVuLmNvbS91YnVudHUvIGZvY2FsLXByb3Bvc2VkIG1haW4gcmVzdHJpY3RlZCB1bml2ZXJzZSBtdWx0aXZlcnNlIAoKZGViLXNyYyBodHRwOi8vbWlycm9ycy5hbGl5dW4uY29tL3VidW50dS8gZm9jYWwtYmFja3BvcnRzIG1haW4gcmVzdHJpY3RlZCB1bml2ZXJzZSBtdWx0aXZlcnNlIGZvY2Fs" | base64 -d > /etc/apt/sources.list \
&& apt-get update
RUN DEBIAN_FRONTEND=noninteractive  apt-get -y install software-properties-common
RUN add-apt-repository ppa:ondrej/php
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install php8.1
RUN apt-get install -y vim \
&& DEBIAN_FRONTEND=noninteractive apt-get -y install openssh-server \
&& sed -i 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config \
&& echo "PermitRootLogin yes" >> /etc/ssh/sshd_config \
&& echo "root:root" | chpasswd \
&& apt-get install -y php8.1-xdebug \
&& echo "W1hEZWJ1Z10KemVuZF9leHRlbnNpb24gPSB4ZGVidWcuc28KeGRlYnVnLmxvZyAgPSAvdG1wL3hkZWJ1Zy5sb2cKeGRlYnVnLm1vZGUgPSBkZXZlbG9wLGRlYnVnCnhkZWJ1Zy5zdGFydF93aXRoX3JlcXVlc3QgPSB5ZXMKI3hkZWJ1Zy5zdGFydF93aXRoX3JlcXVlc3QgPSB5ZXMgI+W9k+aUueS4unllc+aXtuaJgOacieivt+axgumDveS8mui1sGRlYnVn77yM5LiN6ZyA6KaB6K6+572uaWRla2V5CnhkZWJ1Zy5jbGllbnRfcG9ydCA9IDkwMDMKeGRlYnVnLmNsaWVudF9ob3N0ID0gMTI3LjAuMC4xCnhkZWJ1Zy5yZW1vdGVfaGFuZGxlciA9IGRiZ3AKeGRlYnVnLmNsaV9jb2xvciA9IDIKeGRlYnVnLnZhcl9kaXNwbGF5X21heF9kZXB0aCA9IDE1CnhkZWJ1Zy52YXJfZGlzcGxheV9tYXhfZGF0YSAgPSAyMDQ4" | base64 -d >> /etc/php/8.1/cli/php.ini \
&& echo "W1hEZWJ1Z10KemVuZF9leHRlbnNpb24gPSB4ZGVidWcuc28KeGRlYnVnLmxvZyAgPSAvdG1wL3hkZWJ1Zy5sb2cKeGRlYnVnLm1vZGUgPSBkZXZlbG9wLGRlYnVnCnhkZWJ1Zy5zdGFydF93aXRoX3JlcXVlc3QgPSB5ZXMKI3hkZWJ1Zy5zdGFydF93aXRoX3JlcXVlc3QgPSB5ZXMgI+W9k+aUueS4unllc+aXtuaJgOacieivt+axgumDveS8mui1sGRlYnVn77yM5LiN6ZyA6KaB6K6+572uaWRla2V5CnhkZWJ1Zy5jbGllbnRfcG9ydCA9IDkwMDMKeGRlYnVnLmNsaWVudF9ob3N0ID0gMTI3LjAuMC4xCnhkZWJ1Zy5yZW1vdGVfaGFuZGxlciA9IGRiZ3AKeGRlYnVnLmNsaV9jb2xvciA9IDIKeGRlYnVnLnZhcl9kaXNwbGF5X21heF9kZXB0aCA9IDE1CnhkZWJ1Zy52YXJfZGlzcGxheV9tYXhfZGF0YSAgPSAyMDQ4" | base64 -d >> /etc/php/8.1/apache2/php.ini \
&& apt-get install -y mysql-server \
&& apt-get install -y php8.1-mysql \
&& echo "default_authentication_plugin=mysql_native_password" >> /etc/mysql/mysql.conf.d/mysqld.cnf

CMD  service mysql start && mysql -e "use mysql;update user set authentication_string = '' where user = 'root';ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'smcq123';" -uroot && service mysql restart && service ssh restart && exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"

EXPOSE 80
EXPOSE 22