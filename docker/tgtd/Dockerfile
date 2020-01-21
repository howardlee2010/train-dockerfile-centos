FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="tgtd" build-date="20200121"






    

RUN yum -y install scsi-target-utils \
    && yum clean all && rm -rf /var/cache/yum
RUN sed -i '1 i include /var/lib/cinder/volumes/*' /etc/tgt/tgtd.conf




