FROM kolla/centos-source-cinder-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="cinder-backup" build-date="20200121"






    
        
     



RUN yum -y install nfs-utils \
    && yum clean all && rm -rf /var/cache/yum




USER cinder