FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="sensu-base" build-date="20200121"








RUN usermod --append --home /var/lib/sensu --groups kolla sensu \
    && mkdir -p /var/lib/sensu \
    && chown -R 42467:42467 /var/lib/sensu



    


RUN yum -y install sensu \
    && yum clean all && rm -rf /var/cache/yum

COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start

