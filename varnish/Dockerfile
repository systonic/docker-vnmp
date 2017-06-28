FROM debian:jessie

RUN apt-get update && apt-get install -y curl --no-install-recommends && rm -r /var/lib/apt/lists/*
RUN curl http://repo.varnish-cache.org/GPG-key.txt | apt-key add --
RUN echo "deb http://repo.varnish-cache.org/debian/ jessie varnish-4.1" >> /etc/apt/sources.list.d/varnish-cache.list
RUN apt-get update && apt-get install -y varnish --no-install-recommends && rm -r /var/lib/apt/lists/*

#WORKDIR /etc/varnish

COPY docker-entrypoint.sh /usr/local/bin/docker-entrypoint.sh

ENV VCL_CONFIG      /etc/varnish/default.vcl
ENV CACHE_SIZE      64m
ENV VARNISHD_PARAMS -a :80 -T :6082 -S /etc/varnish/secret -p default_ttl=3600 -p default_grace=3600

RUN rm /etc/varnish/default.vcl
VOLUME /etc/varnish/default.vcl

ENTRYPOINT ["docker-entrypoint.sh"]

EXPOSE 80 6082
