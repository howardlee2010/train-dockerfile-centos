FROM kolla/centos-source-prometheus-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-alertmanager" build-date="20200121"




ENV prometheus_alertmanager_version=0.16.1



RUN curl -sSL -o /tmp/prometheus_alertmanager.tar.gz https://github.com/prometheus/alertmanager/releases/download/v${prometheus_alertmanager_version}/alertmanager-${prometheus_alertmanager_version}.linux-amd64.tar.gz \
    && tar xvf /tmp/prometheus_alertmanager.tar.gz -C /opt/ \
    && rm -f /tmp/prometheus_alertmanager.tar.gz \
    && ln -s /opt/alertmanager* /opt/prometheus_alertmanager





USER prometheus