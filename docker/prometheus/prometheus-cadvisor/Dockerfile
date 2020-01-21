FROM kolla/centos-source-prometheus-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-cadvisor" build-date="20200121"






ENV prometheus_cadvisor_version=0.32.0





RUN curl -ssL -o /opt/cadvisor https://github.com/google/cadvisor/releases/download/v${prometheus_cadvisor_version}/cadvisor && chmod 0755 /opt/cadvisor





