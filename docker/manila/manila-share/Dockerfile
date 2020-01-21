FROM kolla/centos-source-manila-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="manila-share" build-date="20200121"






    
        
    

RUN yum -y install ceph-common sqlite \
    && yum clean all && rm -rf /var/cache/yum






USER manila