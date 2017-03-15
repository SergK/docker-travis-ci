FROM ubuntu:xenial

LABEL maintainer "sergey@kulanov.og.ua"

VOLUME /var/lib/docker

RUN apt-get update && \
	apt-get dist-upgrade --yes --force-yes && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    iproute2 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

CMD ["/sbin/init"]
