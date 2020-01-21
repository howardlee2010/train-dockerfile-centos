FROM kolla/centos-source-prometheus-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-openstack-exporter" build-date="20200121"




ENV prometheus_openstack_exporter_version=0.6.0



RUN curl -sSL -o /tmp/prometheus_openstack_exporter.tar.gz https://github.com/openstack-exporter/openstack-exporter/releases/download/v${prometheus_openstack_exporter_version}/openstack-exporter-${prometheus_openstack_exporter_version}.linux-amd64.tar.gz \
    && tar xvf /tmp/prometheus_openstack_exporter.tar.gz -C /opt/ \
    && rm -f /tmp/prometheus_openstack_exporter.tar.gz \
    && ln -s /opt/openstack-exporter* /opt/openstack-exporter





USER prometheus