FROM kolla/centos-source-prometheus-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-memcached-exporter" build-date="20200121"




ENV memcached_exporter_version=0.5.0



RUN curl -sSL -o /tmp/memcached_exporter.tar.gz https://github.com/prometheus/memcached_exporter/releases/download/v${memcached_exporter_version}/memcached_exporter-${memcached_exporter_version}.linux-amd64.tar.gz \
    && tar xvf /tmp/memcached_exporter.tar.gz -C /opt/ \
    && rm -f /tmp/memcached_exporter.tar.gz \
    && ln -s /opt/memcached_exporter* /opt/memcached_exporter





USER prometheus