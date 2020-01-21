FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="skydive-base" build-date="20200121"








RUN usermod --append --home /var/lib/skydive --groups kolla skydive \
    && mkdir -p /var/lib/skydive \
    && chown -R 42468:42468 /var/lib/skydive




    
RUN yum -y install skydive \
    && yum clean all && rm -rf /var/cache/yum



COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start


