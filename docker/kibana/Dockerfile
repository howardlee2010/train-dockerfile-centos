FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="kibana" build-date="20200121"








RUN usermod --append --home /var/lib/kibana --groups kolla kibana \
    && mkdir -p /var/lib/kibana \
    && chown -R 42426:42426 /var/lib/kibana



RUN yum -y install kibana \
    && yum clean all && rm -rf /var/cache/yum

COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start




USER kibana