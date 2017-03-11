FROM centos/systemd

LABEL maintainer "sergey@kulanov.og.ua"

RUN yum update -y && \
	yum -y install e2fsprogs iproute && \
	yum clean all

VOLUME /var/lib/docker

CMD ["/usr/sbin/init"]
