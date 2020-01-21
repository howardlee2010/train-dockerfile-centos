FROM kolla/centos-source-ovn-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ovn-controller" build-date="20200121"






    


RUN yum -y install openvswitch-ovn-host \
    && yum clean all && rm -rf /var/cache/yum


