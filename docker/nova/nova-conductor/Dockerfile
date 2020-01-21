FROM kolla/centos-source-nova-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="nova-conductor" build-date="20200121"







COPY extend_start.sh /usr/local/bin/kolla_nova_extend_start
RUN chmod 755 /usr/local/bin/kolla_nova_extend_start




USER nova