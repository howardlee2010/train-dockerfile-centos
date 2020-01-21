FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="grafana" build-date="20200121"











RUN usermod --append --home /usr/share/grafana --groups kolla grafana \
    && mkdir -p /usr/share/grafana \
    && chown -R 42417:42417 /usr/share/grafana


RUN yum -y install grafana \
    && yum clean all && rm -rf /var/cache/yum

WORKDIR /usr/share/grafana

COPY grafana_sudoers /etc/sudoers.d/kolla_grafana_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start



RUN grafana-cli plugins install gnocchixyz-gnocchi-datasource \
    && grafana-cli plugins install grafana-influxdb-08-datasource



RUN chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/kolla_grafana_sudoers \
    && chmod 755 /usr/local/bin/kolla_extend_start




USER grafana