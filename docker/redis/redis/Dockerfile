FROM kolla/centos-source-redis-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="redis" build-date="20200121"






    

RUN yum -y install redis \
    && yum clean all && rm -rf /var/cache/yum




USER redis