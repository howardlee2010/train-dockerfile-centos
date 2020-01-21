FROM kolla/centos-source-hacluster-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="hacluster-pacemaker-remote" build-date="20200121"






RUN yum -y install pacemaker-remote \
    && yum clean all && rm -rf /var/cache/yum

