FROM kolla/centos-source-prometheus-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-elasticsearch-exporter" build-date="20200121"




ENV elasticsearch_exporter_version=1.0.2



RUN curl -sSL -o /tmp/elasticsearch_exporter.tar.gz https://github.com/justwatchcom/elasticsearch_exporter/releases/download/v${elasticsearch_exporter_version}/elasticsearch_exporter-${elasticsearch_exporter_version}.linux-amd64.tar.gz \
    && tar xvf /tmp/elasticsearch_exporter.tar.gz -C /opt/ \
    && rm -f /tmp/elasticsearch_exporter.tar.gz \
    && ln -s /opt/elasticsearch_exporter* /opt/elasticsearch_exporter





USER prometheus