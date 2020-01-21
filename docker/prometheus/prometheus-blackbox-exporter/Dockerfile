FROM kolla/centos-source-prometheus-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-blackbox-exporter" build-date="20200121"






ENV blackbox_exporter_version=0.14.0



    


RUN yum -y install libcap \
    && yum clean all && rm -rf /var/cache/yum


RUN curl -sSL -o /tmp/blackbox_exporter.tar.gz https://github.com/prometheus/blackbox_exporter/releases/download/v${blackbox_exporter_version}/blackbox_exporter-${blackbox_exporter_version}.linux-amd64.tar.gz \
    && tar xvf /tmp/blackbox_exporter.tar.gz -C /opt/ \
    && rm -f /tmp/blackbox_exporter.tar.gz \
    && ln -s /opt/blackbox_exporter* /opt/blackbox_exporter
RUN setcap cap_net_raw+ep /opt/blackbox_exporter/blackbox_exporter





USER prometheus