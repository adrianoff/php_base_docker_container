FROM nginx:alpine

RUN apk update && apk add wget && apk add bash && rm -rf /var/cache/apk/*

COPY wait-for-it.sh /wait-for-it.sh

WORKDIR "/var/www/adrianoff/php_backend"

EXPOSE 80
EXPOSE 443