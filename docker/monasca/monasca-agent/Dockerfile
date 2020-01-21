FROM kolla/centos-source-monasca-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="monasca-agent" build-date="20200121"







ADD monasca-agent-archive /monasca-agent-source



RUN ln -s monasca-agent-source/* monasca-agent \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /monasca-agent prometheus_client







USER monasca
