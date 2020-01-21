FROM kolla/centos-source-prometheus-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-server" build-date="20200121"




ENV prometheus_version=1.8.2



RUN curl -sSL -o /tmp/prometheus.tar.gz https://github.com/prometheus/prometheus/releases/download/v${prometheus_version}/prometheus-${prometheus_version}.linux-amd64.tar.gz \
    && tar xvf /tmp/prometheus.tar.gz -C /opt/ \
    && rm -f /tmp/prometheus.tar.gz \
    && ln -s /opt/prometheus* /opt/prometheus \
    && mkdir -p /etc/prometheus /data





USER prometheus