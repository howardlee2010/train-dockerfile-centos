# TODO(egonzalez): SFC image is deprecated and will be removed during Queens release
FROM kolla/centos-source-neutron-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="neutron-sfc-agent" build-date="20200121"





COPY extend_start.sh /usr/local/bin/kolla_neutron_extend_start
RUN chmod 755 /usr/local/bin/kolla_neutron_extend_start




USER neutron