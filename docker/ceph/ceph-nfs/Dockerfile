FROM kolla/centos-source-ceph-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ceph-nfs" build-date="20200121"







        


RUN yum -y install nfs-ganesha nfs-ganesha-ceph \
    && yum clean all && rm -rf /var/cache/yum


