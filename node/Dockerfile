FROM node:16-alpine

RUN apk update \
    && apk add --no-cache \
    supervisor \ 
    ;

COPY ./supervisord.conf /etc/supervisord.conf

RUN /bin/sh -c set -eux

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"]

EXPOSE 3000