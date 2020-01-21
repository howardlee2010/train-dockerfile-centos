FROM kolla/centos-source-skydive-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="skydive-analyzer" build-date="20200121"







    
RUN yum -y install skydive-analyzer \
    && yum clean all && rm -rf /var/cache/yum







USER skydive