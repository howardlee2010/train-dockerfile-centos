FROM kolla/centos-source-hacluster-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="hacluster-pcs" build-date="20200121"






RUN yum -y install pcs crmsh \
    && yum clean all && rm -rf /var/cache/yum

