FROM ubuntu:20.04

RUN echo "ZGViIGh0dHA6Ly9taXJyb3JzLmFsaXl1bi5jb20vdWJ1bnR1LyBmb2NhbCBtYWluIHJlc3RyaWN0ZWQgdW5pdmVyc2UgbXVsdGl2ZXJzZSAKCmRlYiBodHRwOi8vbWlycm9ycy5hbGl5dW4uY29tL3VidW50dS8gZm9jYWwtc2VjdXJpdHkgbWFpbiByZXN0cmljdGVkIHVuaXZlcnNlIG11bHRpdmVyc2UgCgpkZWIgaHR0cDovL21pcnJvcnMuYWxpeXVuLmNvbS91YnVudHUvIGZvY2FsLXVwZGF0ZXMgbWFpbiByZXN0cmljdGVkIHVuaXZlcnNlIG11bHRpdmVyc2UgCgpkZWIgaHR0cDovL21pcnJvcnMuYWxpeXVuLmNvbS91YnVudHUvIGZvY2FsLXByb3Bvc2VkIG1haW4gcmVzdHJpY3RlZCB1bml2ZXJzZSBtdWx0aXZlcnNlIAoKZGViIGh0dHA6Ly9taXJyb3JzLmFsaXl1bi5jb20vdWJ1bnR1LyBmb2NhbC1iYWNrcG9ydHMgbWFpbiByZXN0cmljdGVkIHVuaXZlcnNlIG11bHRpdmVyc2UgCgpkZWItc3JjIGh0dHA6Ly9taXJyb3JzLmFsaXl1bi5jb20vdWJ1bnR1LyBmb2NhbCBtYWluIHJlc3RyaWN0ZWQgdW5pdmVyc2UgbXVsdGl2ZXJzZSAKCmRlYi1zcmMgaHR0cDovL21pcnJvcnMuYWxpeXVuLmNvbS91YnVudHUvIGZvY2FsLXNlY3VyaXR5IG1haW4gcmVzdHJpY3RlZCB1bml2ZXJzZSBtdWx0aXZlcnNlIAoKZGViLXNyYyBodHRwOi8vbWlycm9ycy5hbGl5dW4uY29tL3VidW50dS8gZm9jYWwtdXBkYXRlcyBtYWluIHJlc3RyaWN0ZWQgdW5pdmVyc2UgbXVsdGl2ZXJzZSAKCmRlYi1zcmMgaHR0cDovL21pcnJvcnMuYWxpeXVuLmNvbS91YnVudHUvIGZvY2FsLXByb3Bvc2VkIG1haW4gcmVzdHJpY3RlZCB1bml2ZXJzZSBtdWx0aXZlcnNlIAoKZGViLXNyYyBodHRwOi8vbWlycm9ycy5hbGl5dW4uY29tL3VidW50dS8gZm9jYWwtYmFja3BvcnRzIG1haW4gcmVzdHJpY3RlZCB1bml2ZXJzZSBtdWx0aXZlcnNlIGZvY2Fs" | base64 -d > /etc/apt/sources.list \
    && apt-get update
RUN apt-get install -y gcc
RUN apt-get install -y python3 \
    && apt-get install -y pip

CMD  exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"

EXPOSE 80