FROM alpine:3.4

MAINTAINER Vincent Composieux <vincent.composieux@gmail.com>

RUN apk add --update nginx
RUN apk add --no-cache --repository http://nl.alpinelinux.org/alpine/edge/community shadow
RUN rm -rf /var/cache/apk/* && rm -rf /tmp/*

ADD nginx.conf /etc/nginx/
ADD www.conf /etc/nginx/conf.d/
ADD dhparam.pem /etc/ssl/certs/
ADD nginx-selfsigned.crt /etc/ssl/certs
ADD nginx-selfsigned.key /etc/ssl/certs

ARG UID
ARG GUID
RUN adduser -D -g '' -G www-data www-data && \
  chown -R www-data:www-data /var/lib/nginx

RUN chown www-data /var/lib/nginx /var/lib/nginx/tmp


CMD ["nginx"]

EXPOSE 80
EXPOSE 443

