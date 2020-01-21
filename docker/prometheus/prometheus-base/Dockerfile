FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-base" build-date="20200121"








RUN usermod --append --home /var/lib/prometheus --groups kolla prometheus \
    && mkdir -p /var/lib/prometheus \
    && chown -R 42472:42472 /var/lib/prometheus


COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start

