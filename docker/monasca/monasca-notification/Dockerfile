FROM kolla/centos-source-monasca-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="monasca-notification" build-date="20200121"







ADD monasca-notification-archive /monasca-notification-source



RUN ln -s monasca-notification-source/* monasca-notification \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /monasca-notification







USER monasca
