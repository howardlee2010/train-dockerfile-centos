FROM kolla/centos-source-zun-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="zun-compute" build-date="20200121"









RUN yum -y install ceph-common e2fsprogs pciutils xfsprogs \
    && yum clean all && rm -rf /var/cache/yum

COPY zun_sudoers /etc/sudoers.d/kolla_zun_sudoers
COPY extend_start.sh /usr/local/bin/kolla_zun_extend_start

RUN chmod 755 /usr/local/bin/kolla_zun_extend_start \
    && chmod 750 /etc/sudoers.d \
    && chmod 640 /etc/sudoers.d/kolla_zun_sudoers




USER zun