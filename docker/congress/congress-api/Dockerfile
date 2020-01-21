FROM kolla/centos-source-congress-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="congress-api" build-date="20200121"



COPY extend_start.sh /usr/local/bin/kolla_congress_extend_start
RUN chmod 755 /usr/local/bin/kolla_congress_extend_start




USER congress