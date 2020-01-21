FROM kolla/centos-source-monasca-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="monasca-persister" build-date="20200121"







ADD monasca-persister-archive /monasca-persister-source



RUN ln -s monasca-persister-source/* monasca-persister \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /monasca-persister influxdb elasticsearch cassandra-driver







USER monasca
