FROM kolla/centos-source-nova-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="nova-compute-ironic" build-date="20200121"









RUN yum -y install genisoimage \
    && yum clean all && rm -rf /var/cache/yum






USER nova