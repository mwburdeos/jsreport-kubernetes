FROM ubuntu:16.04
MAINTAINER Michael Burdeos <mburdeos@yahoo.com>

ENV	   DEBIAN_FRONTEND="noninteractive" \
      	   SECRETS_DIR="/etc/secrets"

RUN	   mkdir ${SECRETS_DIR} && \
	   apt-get update && \
           apt-get install -y --no-install-recommends apt-utils && \
	   apt-get install -y --no-install-recommends software-properties-common unzip bsdtar curl

RUN        gpg --keyserver pool.sks-keyservers.net --recv-keys B42F6819007F00F88E364FD4036A9C25BF357DD4 && \
           curl -o /usr/local/bin/gosu -fSL "https://github.com/tianon/gosu/releases/download/1.7/gosu-amd64" && \
           curl -o /usr/local/bin/gosu.asc -fSL "https://github.com/tianon/gosu/releases/download/1.7/gosu-amd64.asc" && \
           gpg --verify /usr/local/bin/gosu.asc && \
           rm /usr/local/bin/gosu.asc && \
           chmod +x /usr/local/bin/gosu

RUN	   apt-get install bash && update-alternatives --install /bin/sh sh /bin/bash 100
