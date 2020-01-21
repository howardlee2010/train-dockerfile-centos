FROM kolla/centos-source-designate-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="designate-pool-manager" build-date="20200121"





# The bind9 package here is only to provide the rndc binary.

    
       
    

RUN yum -y install bind \
    && yum clean all && rm -rf /var/cache/yum




USER designate