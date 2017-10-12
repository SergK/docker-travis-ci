FROM debian:jessie

LABEL maintainer "sergey@kulanov.og.ua"

VOLUME /var/lib/docker

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
	apt-get dist-upgrade --yes --force-yes && \
    apt-get install -y --no-install-recommends \
    iproute2 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

CMD ["/sbin/init"]
