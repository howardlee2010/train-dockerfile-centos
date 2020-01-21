FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="dnsmasq" build-date="20200121"






RUN yum -y install dnsmasq \
    && yum clean all && rm -rf /var/cache/yum


