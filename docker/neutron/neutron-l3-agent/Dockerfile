FROM kolla/centos-source-neutron-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="neutron-l3-agent" build-date="20200121"






   
       
   

RUN yum -y install libreswan radvd dibbler-client \
    && yum clean all && rm -rf /var/cache/yum






USER neutron