FROM kolla/centos-source-glance-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="glance-api" build-date="20200121"






    


RUN yum -y install qemu-img-ev \
    && yum clean all && rm -rf /var/cache/yum

COPY extend_start.sh /usr/local/bin/kolla_glance_extend_start
RUN chmod 755 /usr/local/bin/kolla_glance_extend_start




USER glance