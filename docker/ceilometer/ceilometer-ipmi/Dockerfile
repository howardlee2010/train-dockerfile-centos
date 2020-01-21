FROM kolla/centos-source-ceilometer-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ceilometer-ipmi" build-date="20200121"






    
        
    



RUN yum -y install ipmitool \
    && yum clean all && rm -rf /var/cache/yum




USER ceilometer