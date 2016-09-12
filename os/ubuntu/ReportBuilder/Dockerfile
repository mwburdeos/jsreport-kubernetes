# Implementation of this dockerfile is copied from github
# project jsreport/docker
# - https://github.com/jsreport/docker

FROM jsrnode
MAINTAINER Michael Burdeos (michael.burdeos@oncenter.com)

EXPOSE 5488

###RUN apt-get update && apt-get install -y sudo
###COPY ./.npmrc ~
RUN npm install npm -g

###--This is causing an issue with installing phantomjs
RUN adduser --disabled-password --gecos "" jsreport
###RUN echo "jsreport ALL=(root) NOPASSWD: /usr/local/bin/node" >> /etc/sudoers
###RUN echo "jsreport ALL=(root) NOPASSWD: /usr/local/bin/npm" >> /etc/sudoers

VOLUME ["/jsreport"]

WORKDIR /home/jsreport

ADD run.sh /home/jsreport/run.sh

RUN apt-get install nodejs-legacy -y
RUN apt-get update
RUN apt-get install build-essential -y

RUN npm install jsreport@1.0.9 --production
RUN node node_modules/jsreport --init

RUN npm install jsreport-ejs@1.0.2 --production --save --save-exact
RUN npm install jsreport-jade@2.0.1 --production --save --save-exact
RUN npm install jsreport-freeze@1.0.1 --production --save --save-exact
RUN npm install jsreport-phantom-image@1.0.2 --production --save --save-exact

RUN apt-get install -y xfonts-75dpi
RUN apt-get install -y xfonts-base

RUN apt-get install wkhtmltopdf=0.12.2.4-1 -y
RUN npm install jsreport-wkhtmltopdf@1.1.1 --production --save --save-exact

ENV NODE_ENV production

CMD ["bash", "/home/jsreport/run.sh"]
