FROM node:15.9.0-alpine3.13

RUN apk update \
 && apk --no-cache add openjdk11-jre-headless    \
 && rm -rf /var/cache/apk/*

RUN npm install -g firebase-tools