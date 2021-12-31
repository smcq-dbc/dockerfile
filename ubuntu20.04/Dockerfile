FROM ubuntu:20.04

RUN sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list \
&& apt-get update \
&& apt-get install -y vim

CMD  exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"

EXPOSE 80