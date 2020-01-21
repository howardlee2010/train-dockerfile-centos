FROM kolla/centos-source-neutron-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="neutron-linuxbridge-agent" build-date="20200121"







    



RUN yum -y install bridge-utils ebtables \
    && yum clean all && rm -rf /var/cache/yum




USER neutron